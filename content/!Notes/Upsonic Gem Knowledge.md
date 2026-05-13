[[00_KnowledgeBase/AI/index|index]] 
[[AI Tools]] 
[[40_Inbox/AI Weekend/index]]

# Upsonic Framework — API Reference for Code Generation
# Version: 0.74+ (March 2026)
# Bu dosya Gemini Gem'in Knowledge bölümüne yüklenmek içindir.

## KURULUM

```bash
pip install upsonic groq
```

Ek paketler (gerektiğinde):
- `pip install "upsonic[storage]"` — Memory için (SQLite, PostgreSQL, Redis, MongoDB)
- `pip install "upsonic[rag]"` — Knowledge Base için
- `pip install "upsonic[models]"` — Ek LLM provider'lar için

## DESTEKLENEN MODELLER

Groq (ÜCRETSİZ, varsayılan): "groq/llama-3.3-70b-versatile", "groq/llama-3.1-8b-instant"
OpenAI (ücretli): "openai/gpt-4o-mini", "openai/gpt-4o", "openai/gpt-4.1-mini"
Anthropic: "anthropic/claude-sonnet-4-5"
Google: "google/gemini-2.0-flash"
Ollama (lokal): "ollama/llama3.2"

## TEMEL KAVRAMLAR

### Agent Oluşturma
```python
from upsonic import Agent, Task

agent = Agent(
    model="groq/llama-3.3-70b-versatile",
    name="Agent Adı",
    role="Agent Rolü",
    goal="Agent Hedefi",
    system_prompt="Opsiyonel: Agent'a özel davranış talimatı"  # Opsiyonel
)
```

### Task Oluşturma
```python
task = Task(description="Görev açıklaması")
```

### Agent Çalıştırma
```python
# Sonucu ekrana yazdır
agent.print_do(task)

# Sonucu değişkene al
result = agent.do(task)

# Birden fazla task
results = agent.print_do([task1, task2])
```

## TEAM MODLARI

### Sequential Team (Sıralı)
Görevler sırayla çalışır, context otomatik aktarılır. A → B → C

```python
from upsonic import Agent, Task, Team

agent1 = Agent(model="groq/llama-3.3-70b-versatile", name="Araştırmacı", role="Araştırma Uzmanı", goal="Bilgi toplamak")
agent2 = Agent(model="groq/llama-3.3-70b-versatile", name="Yazar", role="İçerik Yazarı", goal="İçerik üretmek")
agent3 = Agent(model="groq/llama-3.3-70b-versatile", name="Editör", role="İçerik Editörü", goal="İçeriği düzenlemek")

team = Team(
    agents=[agent1, agent2, agent3],
    mode="sequential"
)

tasks = [
    Task(description="Görev 1"),
    Task(description="Görev 2"),
    Task(description="Görev 3")
]

result = team.print_do(tasks)
```

Ne zaman kullanılır: İşler sıralı akıyorsa, her adım bir öncekinin sonucuna bağlıysa.
Örnekler: Blog yazımı, döküman işleme pipeline'ı, veri analiz akışı.

### Coordinate Team (Liderli)
Bir lider agent strateji oluşturur, görevleri dağıtır, sonuçları birleştirir.

```python
from upsonic import Agent, Task, Team

analyst = Agent(model="groq/llama-3.3-70b-versatile", name="Analist", role="Pazar Analisti", goal="Pazarı analiz etmek")
creative = Agent(model="groq/llama-3.3-70b-versatile", name="Kreatif", role="İçerik Üretici", goal="İçerik üretmek")
strategist = Agent(model="groq/llama-3.3-70b-versatile", name="Stratejist", role="Strateji Uzmanı", goal="Strateji belirlemek")

team = Team(
    agents=[analyst, creative, strategist],
    mode="coordinate",
    model="groq/llama-3.3-70b-versatile"  # ZORUNLU: Lider agent için model
)

tasks = [
    Task(description="Görev 1"),
    Task(description="Görev 2"),
    Task(description="Görev 3")
]

result = team.print_do(tasks)
```

Özel lider belirlemek (opsiyonel):
```python
leader = Agent(model="groq/llama-3.3-70b-versatile", name="Proje Yöneticisi", role="Lider", goal="Ekibi yönetmek")
team = Team(agents=[analyst, creative], mode="coordinate", model="groq/llama-3.3-70b-versatile", leader=leader)
```

Ne zaman kullanılır: Birden fazla uzman paralel çalışıp sonuçlar birleştirilecekse.
Örnekler: Kampanya planlama, proje yönetimi, çok boyutlu analiz.

### Route Team (Yönlendirmeli)
Router gelen soruyu en uygun uzmana yönlendirir. Uzmanlar birbirinden habersiz.

```python
from upsonic import Agent, Task, Team

billing = Agent(
    model="groq/llama-3.3-70b-versatile",
    name="Fatura Uzmanı",
    role="Faturalama Uzmanı",
    goal="Fatura sorunlarını çözmek",
    system_prompt="Sen fatura, ödeme ve abonelik konularında uzman bir destek temsilcisisin."
)

tech = Agent(
    model="groq/llama-3.3-70b-versatile",
    name="Teknik Uzman",
    role="Teknik Destek Uzmanı",
    goal="Teknik sorunları çözmek",
    system_prompt="Sen yazılım hataları ve teknik problemlerde uzman bir destek temsilcisisin."
)

team = Team(
    agents=[billing, tech],
    mode="route",
    model="groq/llama-3.3-70b-versatile"  # ZORUNLU: Router agent için model
)

task = Task(description="Kullanıcı sorusu")
result = team.print_do(task)
```

Özel router belirlemek (opsiyonel):
```python
router = Agent(model="groq/llama-3.3-70b-versatile", name="Yönlendirici", role="Router", goal="Soruyu doğru uzmana yönlendirmek")
team = Team(agents=[billing, tech], mode="route", model="groq/llama-3.3-70b-versatile", router=router)
```

Ne zaman kullanılır: Gelen isteği doğru uzmana yönlendirme gerekiyorsa.
Örnekler: Müşteri destek, help desk, soru kategorilendirme.

### Manuel Çağrı (Team Olmadan)
Agent'ları doğrudan kodda çağırarak sonuçları aktarma.

```python
from upsonic import Agent, Task

agent1 = Agent(model="groq/llama-3.3-70b-versatile", name="Analist", role="Veri Analisti", goal="Veriyi analiz etmek")
agent2 = Agent(model="groq/llama-3.3-70b-versatile", name="Raporcu", role="Rapor Yazarı", goal="Rapor yazmak")

# Adım 1
task1 = Task(description="Veriyi analiz et")
result1 = agent1.do(task1)

# Adım 2 — önceki sonucu kullan
task2 = Task(description=f"Bu sonuçlardan rapor yaz: {result1}")
agent2.print_do(task2)
```

Ne zaman kullanılır: Çok basit, 1-2 agent yeterliyse; tam kontrol isteniyorsa.

## MEMORY (HAFIZA)

```python
from upsonic import Agent, Task
from upsonic.storage import Memory, InMemoryStorage

memory = Memory(
    storage=InMemoryStorage(),
    session_id="session_001",
    full_session_memory=True
)

agent = Agent(model="groq/llama-3.3-70b-versatile", memory=memory)

agent.print_do(Task(description="Benim adım Ali"))
agent.print_do(Task(description="Benim adım ne?"))  # Hatırlar: "Ali"
```

## CULTURE (KÜLTÜR/DAVRANIŞ KURALLARI)

```python
from upsonic import Agent, Task, Culture

culture = Culture(
    user_description="Bu bir Türk fintech şirketinin destek agent'ıdır. Nazik ve profesyonel ol. Türkçe cevap ver. Rakipler hakkında yorum yapma.",
    model="groq/llama-3.3-70b-versatile"
)

agent = Agent(
    model="groq/llama-3.3-70b-versatile",
    name="Destek Asistanı",
    culture=culture
)
```

## NESTED TEAMS (İÇ İÇE TAKIMLAR)

```python
from upsonic import Agent, Task, Team

# Alt takım 1
research_team = Team(
    agents=[researcher1, researcher2],
    mode="sequential",
    name="Araştırma Takımı"
)

# Alt takım 2
content_team = Team(
    agents=[writer, editor],
    mode="sequential",
    name="İçerik Takımı"
)

# Üst takım — entities parametresi ile Team içine Team koyulur
main_team = Team(
    entities=[research_team, content_team],
    mode="coordinate",
    model="groq/llama-3.3-70b-versatile"
)
```

## GOOGLE COLAB İÇİN KURULUM BLOĞU

Her kodun başına bu kurulum hücresini ekle:
```python
# Google Colab'da çalıştırmak için önce bu hücreyi çalıştırın:
!pip install -q upsonic openai groq

import os
os.environ["GROQ_API_KEY"] = "YOUR_KEY_HERE"  # console.groq.com'dan ücretsiz alın
# OpenAI kullanmak isterseniz:
# os.environ["OPENAI_API_KEY"] = "YOUR_KEY_HERE"
```

## YÖNTEM SEÇİM REHBERİ

| Senaryo | Önerilen Yöntem |
|---------|----------------|
| Basit tek görev | Tek Agent |
| 2 adımlı basit iş | Manuel Çağrı |
| Sıralı pipeline (araştır→yaz→düzenle) | Sequential Team |
| Paralel uzmanlar + birleştirme | Coordinate Team |
| Soruyu doğru uzmana yönlendirme | Route Team |
| Karmaşık hiyerarşik workflow | Nested Teams |