# LOGO - Frontend Developer Assessment

## 🎯 Descripción

Solución a los ejercicios técnicos.

## Tips

- Cada ejercicio corresponde a un nuevo directorio y repositorio de git independiente.
- Se evaluará acorde con lo que se describe aquí.
- Lee todo con concentración. Toda la información que necesitas está vinculada aquí, por lo que evita buscar otros tutoriales.
- **NO USES LLMS PARA ESTA PRUEBA**. Esta prueba no se trata de velocidad, sino de las preguntas que se realizarán después de la prueba. Tómate todo el tiempo necesario para programarlo a mano.
- Haz un commit por paso completado (que equivale a una feature). No se aceptarán commits con varios features, pero puedes tener tantos commit de 'fix' como quieras. No sobreescribas la historia de git.
- El resultado ha de ser un link a un repositorio de git público.
- Los ejercicios dependen el uno del otro, por lo que ejecútalos en orden.

## 📋 Ejercicios

### Ejercicio 1: Setup

- Tutorial Svelte completo (Basic Svelte + Basic SvelteKit)
- Proyecto SvelteKit inicializado (TypeScript + Tailwind)

### Ejercicio 2: MVP Frutería

- 5 productos con botones de compra
- Sistema de carrito funcional
- Cálculo automático del total
- liminación individual de items

## Creating a project

```sh
# create a new project in the current directory
npx sv create

# create a new project in my-app
npx sv create my-app
```

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```sh
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```sh
npm run build
```

You can preview the production build with `npm run preview`.
