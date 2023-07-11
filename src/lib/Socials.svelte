<script lang="ts">
  import { Button } from "spaper";
</script>

<div class="row flex-right at-t4">
  <Button
    class="animate__animated animate__jello animate__delay-1s animate__repeat-2"
    href="https://github.com/okoliken"
    target="_blank"
  >
    Github
  </Button>
  <Button
    class="animate__animated animate__swing animate__delay-1s animate__repeat-2"
    href="https://twitter.com/jeff_okoli"
    target="_blank"
  >
    Twitter
  </Button>
  <Button
    class="animate__animated animate__tada animate__delay-1s animate__repeat-2"
    href="https://www.linkedin.com/in/okoli-jahbuchim-0b1719224/"
    target="_blank"
  >
    LinkedIn
  </Button>
</div>

<style>
  .at-t4 {
    transform: translateX(-10px) translateY(40px);
  }

  :global(a){
    margin-right: 6px;
  }
</style>
