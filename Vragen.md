```dataviewjs
const pages = dv.pages();
let output = [];

for (let page of pages) {
    const file = app.vault.getAbstractFileByPath(page.file.path);
    if (file && file.path.endsWith(".md")) {
        const content = await app.vault.read(file);
        const lines = content.split("\n");

        for (let i = 0; i < lines.length; i++) {
            if (lines[i].startsWith("#?")) {
                const vraag = lines[i].replace("#?", "").trim();
                const antwoord = (i + 1 < lines.length && lines[i + 1].trim() !== "" && !lines[i + 1].startsWith("#"))
                    ? lines[i + 1].trim()
                    : null;

                let blok = vraag;
                if (antwoord) {
                    blok += `\n${antwoord}`;
                }
                blok += `\n[[${page.file.name}]]`;

                output.push(blok);
            }
        }
    }
}

dv.paragraph(output.join("\n\n"));
