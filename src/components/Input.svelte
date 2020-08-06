<script>
  export let id;
  export let value;
  export let label;
  export let error = "";
  export let type = "text";
</script>

<style>
  .field {
    position: relative;

    --transition: 150ms cubic-bezier(0.4, 0, 0.2, 1);
    --color: #1a73e8;
    --lebel-spacing: 0.6rem;
    --input-height: 38px;

    --label-has-value-transform: translate(
        -6px,
        calc(-1 / 2 * var(--input-height) - 10px)
      )
      scale(0.85);
  }

  label.hasValue {
    transform: var(--label-has-value-transform);
  }
  .field:focus-within label {
    transform: var(--label-has-value-transform);
    color: var(--color);
  }
  .field:focus-within input {
    outline: none;
    box-shadow: inset 0 0 0 2px var(--color);
  }

  label {
    position: absolute;
    top: calc(var(--input-height) / 2 + 2px);
    transform: translateY(-50%);
    transform-origin: bottom left;
    left: var(--lebel-spacing);
    background-color: #fff;
    padding: 0 6px;
    color: #5f6368;
    font-size: 14px;
    transition: var(--transition);
    transition-property: transform, color;
    cursor: text;
    user-select: none;
  }

  input {
    font-size: 1rem;
    padding: 0.2rem var(--lebel-spacing);
    border: none;
    box-shadow: inset 0 0 0 1px #dadce0;
    border-radius: 4px;
    transition: var(--transition);
    transition-property: box-shadow;
    height: var(--input-height);
    width: 100%;
  }

  .error {
    color: red;
    font-size: 12px;
    padding-top: 8px;
  }
</style>

<div class="field">
  <label for={id} class={value ? 'hasValue' : ''}>{label}</label>
  <input {id} {type} on:change />
  {#if error}
    <div class="error">{error}</div>
  {/if}
</div>
