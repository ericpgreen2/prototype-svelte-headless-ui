<script lang="ts">
  import BasicDialog from "./BasicDialog.svelte";
  import CompoundDialog from "./CompoundDialog.svelte";
</script>

<div class="bg-blue-500 h-screen">
  <h1 class="bg-pink-500">This page is for testing dialogs.</h1>

  <div class="flex gap-x-2">
    <BasicDialog />

    <CompoundDialog />
  </div>
</div>
