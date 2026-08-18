
```dataviewjs
// 1. Fetch all pages inside the "3- Notes" folder
let pages = dv.pages('"3- Notes"');

let tagsMap = {};

for (let page of pages) {
    let isMatch = false;
    
    // Check if the frontmatter 'link' matches AWS
    if (page.link) {
        if (Array.isArray(page.link)) {
            isMatch = page.link.some(l => l.path.endsWith("AWS.md") || l.display === "AWS");
        } else {
            isMatch = page.link.path.endsWith("AWS.md") || page.link.display === "AWS";
        }
    }

    // If it links to AWS, process its frontmatter 'tag' field
    if (isMatch && page.tag) {
        let tags = Array.isArray(page.tag) ? page.tag : [page.tag];

        for (let tagLink of tags) {
            if (tagLink.path) {
                // Extract file name without directory or extension (preserves casing)
                let tagName = tagLink.path.split("/").pop().replace(".md", "");

                if (!tagsMap[tagName]) {
                    tagsMap[tagName] = [];
                }
                
                // Add the note link to this tag group if not already added
                if (!tagsMap[tagName].some(item => item.path === page.file.link.path)) {
                    tagsMap[tagName].push(page.file.link);
                }
            }
        }
    }
}

// 2. Render headers and lists dynamically
let sortedTags = Object.keys(tagsMap).sort();

if (sortedTags.length === 0) {
    dv.paragraph("*No notes found linking to AWS.*");
} else {
    for (let tag of sortedTags) {
        // Injects a clean new line before rendering the header
        dv.paragraph("\n");
        // Creates the ## Heading style using the tag's original casing
        dv.header(2, tag); 
        // Lists the matching notes below it
        dv.list(tagsMap[tag]); 
    }
}
```

