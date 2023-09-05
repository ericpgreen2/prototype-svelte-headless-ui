<script lang="ts">
  const routes = [
    {
      name: "Dialog",
      path: "/dialog",
    },
    {
      name: "Popover",
      path: "/popover",
    },
    {
      name: "Tabs",
      path: "/tabs",
    },
  ];
</script>

<nav>
  <ul>
    {#each routes as route}
      <li>
        <a href={route.path}>{route.name}</a>
      </li>
    {/each}
  </ul>
</nav>
