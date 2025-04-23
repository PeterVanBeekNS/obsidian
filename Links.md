```dataviewjs
const pages = dv.pages();
let allLinks = [];

for (let page of pages) {
    const filePath = page.file.path;

    if (filePath.endsWith(".md")) {
        const file = app.vault.getAbstractFileByPath(filePath);
        const content = await app.vault.read(file);
        const lines = content.split("\n");

        for (let line of lines) {
            const match = line.match(/^(.*?)\s+#link\s+(https?:\/\/\S+)/);
            if (match) {
                const description = match[1].trim();
                const url = match[2].trim();
                allLinks.push({
                    file: page.file.name,
                    description,
                    url
                });
            }
        }
    }
}

dv.header(2, "🔗 Alle gelabelde links (#link)");
dv.list(allLinks.map(link =>
  `**${link.description}** — [${link.url}](${link.url}) in [[${link.file}]]`
));


