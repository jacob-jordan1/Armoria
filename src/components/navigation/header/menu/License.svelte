<script lang="ts">
  // @ts-check
  import {t} from "svelte-i18n";
  import {state} from "data/stores";
  import NavButton from "../shared/NavButton.svelte";

  const showLicense = () => {
    $state.license = 1;
  };
</script>

<NavButton value="license" label={$t(`menu.license`)} onclick={showLicense} tip={$t("tooltip.license")} />
