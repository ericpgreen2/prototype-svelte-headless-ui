<script lang="ts">
  import {
    Dialog,
    DialogOverlay,
    DialogTitle,
  } from "@rgossiaux/svelte-headlessui";

  let open = false;

  function close() {
    open = false;
  }
</script>

<button on:click={() => (open = true)} class="border p-2">
  Open basic dialog
</button>

<Dialog
  {open}
  on:close={close}
  class="fixed inset-0 flex items-center justify-center"
>
  <DialogOverlay
    class="fixed inset-0 bg-gray-300 transition-opacity opacity-30"
  />
  <div
    class="transform p-6 bg-white rounded-md max-w-lg w-full shadow border border-slate-300 flex flex-col"
  >
    <DialogTitle class="text-gray-800 text-lg font-semibold leading-7 mb-4"
      >Deploy your project to Rill Cloud</DialogTitle
    >
    <p>
      Run this command from your project directory. <a
        href="docs"
        class="text-blue-500">See docs.</a
      >
    </p>

    <div class="flex mt-2">
      <div class="grow" />
      <button on:click={close} class="border py-2 px-3">Close</button>
    </div>
  </div>
</Dialog>
