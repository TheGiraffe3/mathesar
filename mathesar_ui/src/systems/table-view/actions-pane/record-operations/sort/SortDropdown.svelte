<script lang="ts">
  import type { ComponentProps } from 'svelte';
  import type { Writable } from 'svelte/store';
  import { _ } from 'svelte-i18n';

  import { iconSorting } from '@mathesar/icons';
  import type { Sorting } from '@mathesar/stores/table-data';
  import { BadgeCount, Dropdown, Icon } from '@mathesar-component-library';

  import Sort from './Sort.svelte';

  interface $$Props extends ComponentProps<Dropdown> {
    sorting: Writable<Sorting>;
  }

  export let sorting: Writable<Sorting>;
</script>

<Dropdown
  showArrow={false}
  triggerAppearance="secondary"
  {...$$restProps}
  ariaLabel={$_('sort')}
>
  <svelte:fragment slot="trigger">
    <Icon {...iconSorting} />
    <span class="responsive-button-label">
      {$_('sort')}
      <BadgeCount value={$sorting.size} />
    </span>
  </svelte:fragment>
  <Sort slot="content" {sorting} />
</Dropdown>
