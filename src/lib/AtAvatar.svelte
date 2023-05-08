<script lang="ts">
  import { Popover } from "spaper";

  const getImageUrl = (name: string) => {
    return new URL(`../assets/${name}.jpeg`, import.meta.url).href;
  };
</script>

<Popover label="Atrevido" position="right">
  <img
    class="at-avatar border-6 border-primary shadow
    shadow-hover shadow-large animate__animated animate__bounce animate__delay-1s animate__repeat-2"
    src={getImageUrl("me")}
    alt=""
  />
</Popover>

<style>
  .at-avatar {
    height: 150px;
    width: 150px;
    border-radius: 50%;
  }
</style>
