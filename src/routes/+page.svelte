<script lang="ts">
  import * as NavigationMenu from "#lib/components/ui/navigation-menu/index.js";
  import * as Table from "#lib/components/ui/table/index.js";

  const invoices = [
    {
      invoice: "INV001",
      paymentStatus: "Paid",
      totalAmount: "$250.00",
      paymentMethod: "Credit Card",
    },
    {
      invoice: "INV002",
      paymentStatus: "Pending",
      totalAmount: "$150.00",
      paymentMethod: "PayPal",
    },
    {
      invoice: "INV003",
      paymentStatus: "Unpaid",
      totalAmount: "$350.00",
      paymentMethod: "Bank Transfer",
    },
    {
      invoice: "INV004",
      paymentStatus: "Paid",
      totalAmount: "$450.00",
      paymentMethod: "Credit Card",
    },
    {
      invoice: "INV005",
      paymentStatus: "Paid",
      totalAmount: "$550.00",
      paymentMethod: "PayPal",
    },
    {
      invoice: "INV006",
      paymentStatus: "Pending",
      totalAmount: "$200.00",
      paymentMethod: "Bank Transfer",
    },
    {
      invoice: "INV007",
      paymentStatus: "Unpaid",
      totalAmount: "$300.00",
      paymentMethod: "Credit Card",
    },
  ];

  const geogebraUrl = "https://www.geogebra.org/calculator";
</script>

<svelte:head>
  <title>GeoGebra | Calculadora matemática</title>
  <meta
    name="description"
    content="Calculadora matemática interactiva con GeoGebra"
  />
</svelte:head>

<div class="min-h-screen bg-slate-100 px-4 py-8 sm:px-6 lg:px-10">
  <main class="mx-auto max-w-7xl">
    <!-- Encabezado -->
    <header class="mb-6">
      <h1 class="text-3xl font-bold tracking-tight text-slate-900">
        Calculadora GeoGebra
      </h1>

      <p class="mt-2 text-sm text-slate-600 sm:text-base">
        Explora funciones, gráficas y conceptos matemáticos de manera
        interactiva.
      </p>
    </header>

    <!-- Contenedor del iframe -->
    <section
      class="overflow-hidden rounded-2xl border border-slate-200 bg-white shadow-lg"
    >
      <div
        class="flex items-center justify-between border-b border-slate-200 px-4 py-3"
      >
        <h2 class="font-semibold text-slate-800">Área de trabajo</h2>

        <a
          href={geogebraUrl}
          target="_blank"
          rel="noopener noreferrer"
          class="rounded-lg bg-blue-600 px-4 py-2 text-sm font-medium text-white transition hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2"
        >
          Abrir GeoGebra ↗
        </a>
      </div>

      <div class="w-full bg-white">
        <iframe
          src={geogebraUrl}
          title="Calculadora gráfica de GeoGebra"
          class="h-[500px] w-full border-0 sm:h-[650px] lg:h-[750px]"
          allowfullscreen
          loading="lazy"
        ></iframe>
      </div>
    </section>

    <!-- Información inferior -->
    <p class="mt-4 text-sm text-slate-500">
      Herramienta educativa para explorar gráficas y resolver ejercicios
      matemáticos.
    </p>
  </main>
</div>

<NavigationMenu.Root>
  <NavigationMenu.List>
    <NavigationMenu.Item>EcoConsumo</NavigationMenu.Item>
    <NavigationMenu.Item>
      <NavigationMenu.Trigger>Documentación</NavigationMenu.Trigger>
      <NavigationMenu.Content>
        <ul class="grid w-50 gap-2 p-4 md:w-75">
          <li>
            <NavigationMenu.Link
              href="https://www.shadcn-svelte.com/docs/components"
              class="block select-none rounded-md p-3 leading-none no-underline outline-none transition-colors hover:bg-accent hover:text-accent-foreground focus:bg-accent focus:text-accent-foreground"
            >
              Shadcn Svelte
            </NavigationMenu.Link>
          </li>
          <li>
            <NavigationMenu.Link
              href="https://svelte.dev/tutorial/svelte/welcome-to-svelte"
              class="block select-none rounded-md p-3 leading-none no-underline outline-none transition-colors hover:bg-accent hover:text-accent-foreground focus:bg-accent focus:text-accent-foreground"
            >
              Tutorial Svelte
            </NavigationMenu.Link>
          </li>
          <li>
            <NavigationMenu.Link
              href="https://tailwindcss.com/"
              class="block select-none rounded-md p-3 leading-none no-underline outline-none transition-colors hover:bg-accent hover:text-accent-foreground focus:bg-accent focus:text-accent-foreground"
            >
              Tailwind CSS
            </NavigationMenu.Link>
          </li>
        </ul>
      </NavigationMenu.Content>
    </NavigationMenu.Item>
  </NavigationMenu.List>
</NavigationMenu.Root>

<Table.Root class="bg-secondary">
  <Table.Caption>A list of your recent invoices.</Table.Caption>
  <Table.Header>
    <Table.Row>
      <Table.Head class="w-[100px]">Invoice</Table.Head>
      <Table.Head>Status</Table.Head>
      <Table.Head>Method</Table.Head>
      <Table.Head class="text-end">Amount</Table.Head>
    </Table.Row>
  </Table.Header>
  <Table.Body>
    {#each invoices as invoice (invoice)}
      <Table.Row>
        <Table.Cell class="font-medium">{invoice.invoice}</Table.Cell>
        <Table.Cell>{invoice.paymentStatus}</Table.Cell>
        <Table.Cell>{invoice.paymentMethod}</Table.Cell>
        <Table.Cell class="text-end">{invoice.totalAmount}</Table.Cell>
      </Table.Row>
    {/each}
  </Table.Body>
  <Table.Footer>
    <Table.Row>
      <Table.Cell colspan={3}>Total</Table.Cell>
      <Table.Cell class="text-end">$2,500.00</Table.Cell>
    </Table.Row>
  </Table.Footer>
</Table.Root>
