---
title: Apresentação do Projeto Presence
author: Viktor Marinho, Daniel Henrique, Guilherme Abe.
layout: cover
fonts:
  sans: 'Robot'
  serif: 'Robot Slab'
  mono: 'Fira Code'
---

<img src="https://raw.githubusercontent.com/viktormarinho/deco-apps/main/presence/logo.png" style="filter: invert()" width="225" height=""/>

**Otimize a conversão do seu e-commerce com Gatilhos Emocionais de Social Proof
em Tempo Real**

---

<br>
<br>
<br>
<br>

<div style="display: flex; align-items: center; gap: 4rem; justify-content: center;">
  <div style="display: flex; align-items: center; flex-direction: column; gap: 1rem;">
  <div style="display: flex; align-items: end; gap: 1rem; margin-top: 2rem">
  <img src="https://raw.githubusercontent.com/deco-cx/apps/main/decohub/logo.png" style="" width="150" height=""/>
  <svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-apps" width="48" height="48" viewBox="0 0 24 24" stroke-width="2" stroke="green" fill="none" stroke-linecap="round" stroke-linejoin="round">
  <path stroke="none" d="M0 0h24v24H0z" fill="none"/>
  <path d="M4 4m0 1a1 1 0 0 1 1 -1h4a1 1 0 0 1 1 1v4a1 1 0 0 1 -1 1h-4a1 1 0 0 1 -1 -1z"/>
  <path d="M4 14m0 1a1 1 0 0 1 1 -1h4a1 1 0 0 1 1 1v4a1 1 0 0 1 -1 1h-4a1 1 0 0 1 -1 -1z"/>
  <path d="M14 14m0 1a1 1 0 0 1 1 -1h4a1 1 0 0 1 1 1v4a1 1 0 0 1 -1 1h-4a1 1 0 0 1 -1 -1z"/>
  <path d="M14 7l6 0"/>
  <path d="M17 4l0 6"/>
  </svg>
  </div>
  <h5>Deco Apps</h5>
  </div>
  <img src="https://raw.githubusercontent.com/viktormarinho/deco-apps/main/presence/logo.png" style="filter: invert()" width="200" height=""/>
</div>

<br>
<br>
<br>

<h4 style="text-align: center;">
Plug and Play de Sections, Handlers e Actions para o seu site deco.cx
</h4>

<br>

<h5 style="text-align: center;">
  <span style="color: dodgerblue; text-decoration: underline;">Pull request #188</span>
</h5>

---

<h2 style="text-align:center; margin-top: 12rem;">Mão na massa</h2>

<img src="https://raw.githubusercontent.com/viktormarinho/deco-apps/main/presence/logo.png" style="filter: invert(); position: absolute; bottom: 2rem; right: 2rem;" width="150" height=""/>
---

## Configuração

Para começar, configure o Handler do Presence de acordo com suas necessidades.

Aqui está um exemplo de como você faria isso:

```bash
├── apps
├── components
├── islands
├── loaders
├── routes
  └── presence
    └── index.ts   <-- Crie este arquivo
├── sdk
├── sections
└── static
```

```ts
import { createPresenceHandler } from "apps/presence/infra/presenceRoom.ts";

export const handler = createPresenceHandler({});
```

<img src="https://raw.githubusercontent.com/viktormarinho/deco-apps/main/presence/logo.png" style="filter: invert(); position: absolute; bottom: 2rem; right: 2rem;" width="150" height=""/>
---

Se você deseja ir mais a
fundo, o Presence permite que você se conecte a alguns eventos, como quando
ocorre um erro (útil para registro e métricas), ou quando o servidor WebSocket
transmite mensagens para uma sala (útil para estender o comportamento).

Aqui está um exemplo mais complexo:

```ts
export const handler = createPresenceHandler({
  onError: (e) => {
    someLogService.registerError(e);
  },
  onRoomStateChange: (room) => {
    otherRealtimeService.notifyStateChange(room.connections);
  },
});
```

<img src="https://raw.githubusercontent.com/viktormarinho/deco-apps/main/presence/logo.png" style="filter: invert(); position: absolute; bottom: 2rem; right: 2rem;" width="150" height=""/>
---

Agora você pode usar qualquer Seção do Presence, e elas usarão o Handler
configurado anteriormente para rastrear toda a lógica em tempo real necessária.

Por exemplo, se você deseja exibir a Seção PresenceCounter, que mostra um
contador de quantas pessoas estão na página atual (útil para gatilhos de Prova
Social), você pode usá-la assim:

```bash
├── apps
├── components
├── islands
  └── Presence
    └── PresenceCounter.tsx   <-- Crie este arquivo
├── loaders
├── routes
├── sdk
├── sections
└── static
```

```ts
export { type Props } from "apps/presence/sections/Presence/PresenceCounter.tsx";
export { default } from "apps/presence/sections/Presence/PresenceCounter.tsx";
```

<img src="https://raw.githubusercontent.com/viktormarinho/deco-apps/main/presence/logo.png" style="filter: invert(); position: absolute; bottom: 2rem; right: 2rem;" width="150" height=""/>
---

<br>
<br>
<br>
<br>

```ts
export { type Props } from "apps/presence/sections/Presence/PresenceCounter.tsx";
export { default } from "apps/presence/sections/Presence/PresenceCounter.tsx";
```

Por quê esse re-export é necessário?

<img src="https://fresh.deno.dev/logo.svg?__frsh_c=04a5b2c5ca2fac3ddfb2d75553b44aae75c5778a" />

O Fresh não permitirá que nenhum Aplicativo Deco externo crie uma Island, a
menos que você o reexporte explicitamente na pasta Islands, portanto, esta etapa
é necessária para que o componente funcione corretamente.

<img src="https://raw.githubusercontent.com/viktormarinho/deco-apps/main/presence/logo.png" style="filter: invert(); position: absolute; bottom: 2rem; right: 2rem;" width="150" height=""/>

---

<h2 style="text-align:center; margin-top: 12rem;">
Começe a otimizar a conversão do seu e-commerce com o Presence hoje, na deco!
</h2>

<img src="https://raw.githubusercontent.com/viktormarinho/deco-apps/main/presence/logo.png" style="filter: invert(); position: absolute; bottom: 2rem; right: 2rem;" width="150" height=""/>
