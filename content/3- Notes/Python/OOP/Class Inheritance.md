A class can inherit attributes and methods from a parent class. The parent class is called **Super Class**.

```python
class Fish(Animal):
	def __init__(self):
		super().__init__()
```

In this example, "Animal" is the super class. When the Fish is initializing, it also inherits everything under Animal's init by using `super().__init__()`


## Inheriting a Method
```python
class Animal:
	def __init__(self):
		self.num_eyes = 2
	def breathe(self):
		print("Inhale, exhale")
		
		

class Fish(Animal):
	def __init__(self):
		super().__init__()
		
	def breathe(self):
		super().breathe() # We inherited the function, but added additional functionality
		print("but underwater")
		
```

By doing it like this, we inherited the init and the breathe(). We also changed the breathe() method by using additional parameters and by using the same name