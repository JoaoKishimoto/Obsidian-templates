---
created: 10-07-2025
modified: 12-05-2026
---
<%*
let filePath = tp.file.path(true); // Obtém o caminho do arquivo atual
let file = app.vault.getAbstractFileByPath(filePath);

let newContent = `- [ ] Task \n`;
// Adiciona o conteúdo ao final do arquivo 
await app.vault.append(file, newContent);	
%>

