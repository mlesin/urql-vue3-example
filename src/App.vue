<template>
  <Suspense>
    <template #default>
      <PokemonList />
    </template>
    <template #fallback>
      <div>Loading...</div>
    </template>
  </Suspense>
</template>

<script>
import { defaultExchanges, provideClient } from "@urql/vue";
import PokemonList from "./PokemonList.vue";
import { devtoolsExchange } from "@urql/devtools";

export default {
  name: "App",
  setup() {
    provideClient({
      url: "https://trygql.formidable.dev/graphql/basic-pokedex",
      exchanges: [devtoolsExchange, ...defaultExchanges],
    });
  },
  components: {
    PokemonList,
  },
};
</script>
