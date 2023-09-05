<script lang="ts">
  import {
    Popover,
    PopoverButton,
    PopoverPanel,
  } from "@rgossiaux/svelte-headlessui";
  import { createPopperActions } from "svelte-popperjs";

  // Data for base Popover
  const menuItems = [
    { name: "Account settings" },
    { name: "Support" },
    { name: "License" },
    { name: "Logout" },
  ];

  // Data for nested Popover
  let searchBox: string = "";
  const users = [
    { name: "John" },
    { name: "Jane" },
    { name: "Eric" },
    { name: "Nishant" },
  ];

  // Positioning the nested Popover
  const [popperRef, popperContent] = createPopperActions();
  const popperOptions = {
    placement: "auto",
    strategy: "fixed",
    modifiers: [{ name: "offset", options: { offset: [0, 8] } }],
  };
</script>

<Popover class="flex flex-col gap-y-4">
  <PopoverButton class="h-10 w-10 bg-blue-500 rounded-full text-[10px]"
    >Icon button</PopoverButton
  >

  <div class="flex gap-x-4">
    <PopoverPanel
      use={[popperRef]}
      class="max-w-fit z-10 border p-2 bg-yellow-300"
    >
      <ul>
        {#each menuItems as item}
          <li>{item.name}</li>
        {/each}
        <li>
          <Popover class="flex items-start gap-x-4">
            <PopoverButton>View as</PopoverButton>
            <PopoverPanel
              use={[[popperContent, popperOptions]]}
              class="z-10 border p-2 bg-pink-500"
            >
              <input bind:value={searchBox} />
              <ul>
                {#each users as result}
                  <li>{result.name}</li>
                {/each}
              </ul>
            </PopoverPanel>
          </Popover>
        </li>
      </ul>
    </PopoverPanel>
  </div>
</Popover>
