<!-- src/routes/upload.svelte -->
<script>
  import FileDropzone from 'svelte-file-dropzone';

  let files = [];
  let instructions = '';

  const handleFilesAdded = (event) => {
    files = [...files, ...event.detail.addedFiles];
  };

  const handleSubmit = () => {
    console.log('Uploaded files:', files);
    console.log('Instructions:', instructions);
  };
</script>

<div class="container mx-auto max-w-3xl p-4">
  <h1 class="text-3xl font-bold mb-4">Upload Files and Enter Instructions</h1>

  <FileDropzone on:addedfile={handleFilesAdded} />

  <div class="mt-4">
    <textarea
      class="textarea textarea-bordered w-full h-48"
      bind:value={instructions}
      placeholder="Instructions"
    />
  </div>

  <button class="btn btn-primary mt-4" on:click={handleSubmit}>Submit</button>
</div>