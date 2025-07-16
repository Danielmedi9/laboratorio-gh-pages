Breve resumen del ejercicio 1 despliegue manual de github pages:

Comienzo con subir el proyecto a un repositorio.

Añado en viteconfig la base

```vite.config.ts
export default defineConfig({
  envPrefix: 'PUBLIC_',
  base: './',
  plugins: [
    TanStackRouterVite({
      routesDirectory: 'src/scenes',
      generatedRouteTree: 'src/core/router/route-tree.ts',
      autoCodeSplitting: true,
    }),
    react({
      babel: {
        plugins: ['@emotion'],
      },
    }),
  ],
});
```

Configuro el HashHistory en la carmera router.ts

```router.ts
const history = createHashHistory();

export const router = createRouter({
  routeTree,
  history,
});

declare module '@tanstack/react-router' {
  interface Register {
    router: typeof router;
  }
}
```

Subo los cambios, hago un build y creo la rama gh-pages.
En la rama gh-pages solo dejo los archivos dentro del dist y subo al reposirotio.
Luego en settings de github seccion pages en branch eligo la rama gh-pages y /(root) guardo y espero unos minutos hasta que se inicialice el repositorio.
