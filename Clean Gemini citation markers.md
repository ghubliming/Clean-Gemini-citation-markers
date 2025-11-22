<%*

// 1. Get the active editor instance

const editor = app.workspace.activeLeaf.view.editor;

  

// 2. Get the entire content of the note

const content = editor.getValue();

  

// 3. Define the Regex pattern to find [cite...] tags

const citationRegex = /\[cite[^\]]*\]/g;

  

// 4. Check if matches exist to avoid unnecessary writes

if (content.match(citationRegex)) {

    // 5. Replace citations

    let cleanContent = content.replace(citationRegex, "");

    // Optional: Fix double spaces that might result from removing tags

    cleanContent = cleanContent.replace(/  +/g, " ");

  

    // 6. Set the new content back to the note

    editor.setValue(cleanContent);

    new Notice("Gemini citations removed from note.");

} else {

    new Notice("No citations found in this note.");

}

%>