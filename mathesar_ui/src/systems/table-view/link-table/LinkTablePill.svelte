<script lang="ts">
  import TableName from '@mathesar/components/TableName.svelte';
  import type { Table } from '@mathesar/models/Table';

  export let table: Pick<Table, 'name'>;
  export let which: 'base' | 'target' | 'mapping';
</script>

<span
  class="table-pill"
  class:base={which === 'base'}
  class:target={which === 'target'}
  class:mapping={which === 'mapping'}
>
  <TableName {table} />
</span>

<style>
  .table-pill {
    border-radius: 500px;
    padding: 0 0.5em;
    margin: 0 0.1em;
    max-width: 100%;
    display: inline-block;
    vertical-align: -20%;
    line-height: 1.2em;
  }
  .base {
    background: var(--base-fill);
    border: solid 1px var(--base-stroke);
  }
  .target {
    background: var(--target-fill);
    border: solid 1px var(--target-stroke);
  }
  .mapping {
    background: var(--mapping-fill);
    border: solid 1px var(--mapping-stroke);
  }
</style>
