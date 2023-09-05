<script lang="ts">
  import { goto } from "$app/navigation";
  import { page } from "$app/stores";
  import { Tab, TabGroup, TabList } from "@rgossiaux/svelte-headlessui";

  const tabs = [
    {
      route: "tab1",
      label: "Tab 1",
    },
    {
      route: "tab2",
      label: "Tab 2",
    },
    {
      route: "tab3",
      label: "Tab 3",
    },
  ];

  // Get the tab index for the current route
  const defaultIndex = tabs.findIndex(
    (tab) => tab.route === $page.params.subpath
  );

  function handleTabChange(detail: CustomEvent) {
    // Navigate to the new tab
    goto(`/tabs/${tabs[detail.detail].route}`);
  }
</script>

<nav class="h-[30px] w-screen bg-blue-300">
  Top navigational bar w/ breadcrumbs
</nav>

<TabGroup {defaultIndex} on:change={handleTabChange}>
  <TabList>
    {#each tabs as tab, i}
      <Tab
        class={({ selected }) =>
          selected
            ? "bg-yellow-200 text-gray-900"
            : "text-gray-500 hover:text-gray-700"}>{tab.label}</Tab
      >
    {/each}
  </TabList>
  <slot />
</TabGroup>
