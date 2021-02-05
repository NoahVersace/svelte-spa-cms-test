<script>
  import { useForm, Validators } from "svelte-use-form";

  const form = useForm({ password: { validators: [Validators.minLength(5)] } });
</script>

<form use:form>
  <input
    name="password"
    class="bg-gray-50 border-gray-400 border-2 rounded p-2"
  />
  <button disabled={!$form.valid} class="bg-purple-300 text-center p-2 rounded"
    >Submit</button
  > <br />
  {#if $form.password.touched && $form.password.errors.minLength}
    The password requires at least {$form.password.errors.minLength} characters.
  {/if}
</form>

<style>
  :global(input.invalid) {
    border-color: red;
  }
  :disabled {
    opacity: 0.5;
  }
</style>
