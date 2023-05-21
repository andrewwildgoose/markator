
<script>
	let files;

	$: if (files) {
		// Note that `files` is of type `FileList`, not an Array:
		// https://developer.mozilla.org/en-US/docs/Web/API/FileList
		console.log(files);

		for (const file of files) {
			console.log(`${file.name}: ${file.size} bytes`);
		}
	}
</script>

<style>	
h1 {
    color: purple;
    font-family: 'Helvetica', sans-serif;
    font-size: 2em;
}
h3 {
    color: purple;
    font-family: 'Helvetica', sans-serif;
    font-size: 1em;
}
.center {
    text-align: center;
    border-radius: 5px;
    border: 2px solid purple;
    margin: auto;
    width: 50%;
    padding: 20px;
}
</style>


<body style="background-color:powderblue;">
    <div class="center">
        <h1 text-align: center>merkator</h1>
        <label for="routeFile"><h3>Upload route files here</h3></label>
        <input
            bind:files
            id="routeFile"
            name='routeFile'
            type="file"
        />

        {#if files}
            <h2>Selected files:</h2>
            {#each Array.from(files) as file}
                <p>{file.name} ({file.size} bytes) </p>
            {/each}
        {/if}
    </div>
</body>