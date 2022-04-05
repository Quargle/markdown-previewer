<!-- Svelte/js -->

<script lang="ts">
	// import { marked } from "../node_modules/marked/lib/marked.esm.js";
	import marked from 'marked';
	// Initial default text
	let markdown:string = `# Welcome to my React Markdown Previewer!

## This is a sub-heading...
### And here's some other cool stuff:

Heres some code, \`<div></div>\`, between 2 backticks.

\`\`\`
// this is multi-line code:

function anotherExample(firstLine, lastLine) {
  if (firstLine == '\`\`\`' && lastLine == '\`\`\`') {
    return multiLineCode;
  }
}
\`\`\`

You can also make text **bold**... whoa!
Or _italic_.
Or... wait for it... **_both!_**
And feel free to go crazy ~~crossing stuff out~~.

There's also [links](https://www.freecodecamp.org), and
> Block Quotes!

And if you want to get really crazy, even tables:

Wild Header | Crazy Header | Another Header?
------------ | ------------- | -------------
Your content can | be here, and it | can be here....
And here. | Okay. | I think we get it.

- And of course there are lists.
  - Some are bulleted.
     - With different indentation levels.
        - That look like this.


1. And there are numbered lists too.
1. Use just 1s if you want!
1. And last but not least, let's not forget embedded images:

![freeCodeCamp Logo](https://cdn.freecodecamp.org/testable-projects-fcc/images/fcc_secondary.svg)
`;

	// The $: below forces this variable to update whenever the referenced value (markdown) changes
	$: renderedMarkdown = marked(markdown, {sanitize: true});

</script>


<!-- Change Tab Title-->
<svelte:head>
	<title>Markdown Previewer</title>
</svelte:head>


<!-- HTML-->
<main>
	<h1>Welcome to my Markdown Previewer</h1>
	<h2>Editor</h2>
	<textarea id="editor" bind:value={markdown}></textarea>
	<h2>Preview</h2>
	<div id="preview">{@html renderedMarkdown}</div>
</main>


<!-- CSS -->
<style>
	main {
		width: 100vw;
		height: 100vh;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin: 0;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 3em;
		font-weight: 100;
		margin: 0rem;
		text-align: center;
		height: auto;
	}

	h2 {
		margin: 0;
		padding: 0.5rem;
	}

	textarea {
		width: 60vw;
		height: 25vh;
		margin: 0;
		border: 1px solid #ccc;
		padding: 1rem;
		overflow-y: scroll;
	}

	#preview {
		width: 60vw;
		height: 40vh;
		margin: 0;
		background-color: #fafafa;
		border: 1px solid #ccc;
		padding: 1rem;
		overflow-y: scroll;
	}
</style>