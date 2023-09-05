<script lang="ts">
  import { page } from "$app/stores";

  $: subpath = $page.params.subpath;
</script>

<h1>Subpath: {subpath}</h1>
