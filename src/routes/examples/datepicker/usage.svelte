<script lang="ts">
  import { Datepicker, P, Label, Select, Button } from "$lib";

  let value = $state<Date | undefined>(undefined);
  let locale = $state("de");
  const locales = [
    { value: "en-US", name: "en-US (US)" },
    { value: "en-GB", name: "en-GB (UK)" },
    { value: "de", name: "de (Germany)" },
    { value: "fr", name: "fr (France)" },
    { value: "ja", name: "ja (Japan)" }
  ];

  const handleSubmit = (event: Event) => {
    event.preventDefault();
    console.log("Selected date:", value ? value.toLocaleDateString(locale) : "None");
  };

  $effect(() => {
    // Only clear if locale is actually changing from a previous value
    if (locale) {
      value = undefined;
    }
  });
</script>

<div class="h-[800px] overflow-visible p-4">
  <h1 class="mb-4 text-xl font-bold">Datepicker Locale Test</h1>
  <form onsubmit={handleSubmit} class="mb-4">
    <Label>
      Choose locale:
      <Select class="mb-4 w-40 rounded p-2" items={locales} bind:value={locale} />
    </Label>

    <Datepicker bind:value {locale} translationLocale={locale} placeholder="Type a date or use calendar" />

    <P class="mt-4 h-96">
      <strong>Selected Locale:</strong>
      {locale}
      <br />
      <strong>Selected Date:</strong>
      {value ? value.toLocaleDateString(locale) : "None"}
    </P>
    <Button type="submit" class="mb-4">Submit</Button>
  </form>

  Lorem ipsum dolor sit amet consectetur, adipisicing elit. Maxime blanditiis voluptatum iste magnam quas quis omnis commodi. Necessitatibus, quidem vitae! Fuga ex molestias assumenda sit dicta quasi officia iusto magni.
</div>
