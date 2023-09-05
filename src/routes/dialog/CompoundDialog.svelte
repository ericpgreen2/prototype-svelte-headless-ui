<script lang="ts">
  import {
    Dialog,
    DialogOverlay,
    DialogTitle,
    Transition,
    TransitionChild,
  } from "@rgossiaux/svelte-headlessui";
  import { slide } from "svelte/transition";

  let open = false;
  function close() {
    open = false;
    selectedConnector = "";
  }

  const connectors = ["one", "two", "three"];
  let selectedConnector = "";

  function chooseConnector(connector: string) {
    console.log(connector);
    selectedConnector = connector;
  }
</script>

<button on:click={() => (open = true)} class="border p-2">
  Open compound dialog
</button>

<!-- Dialog 1 -->
<Transition show={open}>
  <Dialog
    on:close={close}
    class="fixed inset-0 flex items-center justify-center"
  >
    <TransitionChild
      enter="ease-out duration-200"
      enterFrom="opacity-0"
      enterTo="opacity-100"
    >
      <DialogOverlay
        class="fixed inset-0 bg-gray-300 transition-opacity opacity-30"
      />
    </TransitionChild>

    <div
      class="transform p-6 bg-white rounded-md max-w-lg w-full shadow border border-slate-300 flex flex-col"
    >
      <!-- Step 1 -->
      {#if !selectedConnector}
        <DialogTitle class="text-gray-800 text-lg font-semibold leading-7 mb-4"
          >Select a connector</DialogTitle
        >
        <div class="flex gap-x-2">
          {#each connectors as connector}
            <button
              on:click={() => chooseConnector(connector)}
              class="h-16 w-16 bg-green-300"
            />
          {/each}
        </div>
      {/if}

      <!-- Step 2 -->
      {#if selectedConnector}
        <DialogTitle class="text-gray-800 text-lg font-semibold leading-7 mb-4"
          >Connector form: {selectedConnector}</DialogTitle
        >
        <!-- placeholder for tall content -->
        <div
          transition:slide|local={{ duration: 300 }}
          class="w-32 h-96 bg-red-300"
        >
          Form content goes here
        </div>
      {/if}

      <div class="flex mt-2">
        <div class="grow" />
        <button on:click={close} class="border py-2 px-3">Close</button>
      </div>
    </div>
  </Dialog>
</Transition>
