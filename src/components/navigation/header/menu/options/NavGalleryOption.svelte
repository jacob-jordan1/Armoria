<script lang="ts">
  // @ts-check
  import {t} from "svelte-i18n";
  import NavButton from "../../shared/NavButton.svelte";
  import NavItem from "../../shared/NavItem.svelte";
  import Lock from "../../shared/Lock.svelte";
  import {sizes} from "config/options";
  import {size} from "data/stores";

  const changeSize = (value: string | number) => {
    if (typeof value !== "number") return;

    size.set(value);
    localStorage.setItem("size", String(value));
  };
</script>

<div class="container">
  <div class="dropdown level2">
    {#each sizes as [sizeNumber, sizeName]}
      <NavButton selected={sizeNumber === $size} onclick={() => changeSize(sizeNumber)}>
        {$t(`gallery.${sizeName}`)}
      </NavButton>
    {/each}
  </div>

  {#key $size}
    <NavItem tip={$t("tooltip.gallery")}>
      <Lock key="size" />
      {$t(`menu.gallery`)}
    </NavItem>
  {/key}
</div>
