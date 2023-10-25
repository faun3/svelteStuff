<script>
</script>

<button>
  <slot name="icon">*</slot>
  <slot name="text">Placeholder</slot>
</button>

<style lang="scss">
  button {
    padding-block: 0.75em;
    padding-inline: 1.5em;
    border-radius: 10px;
    background-color: teal;
    color: white;
    font-size: 1.15rem;
    font-weight: bold;
    border: none;
    &:active {
      transform: scale(0.95);
    }
    &:hover {
      background-color: blue;
    }
  }
</style>
