---
title: Apresentação do Projeto Presence
author: Viktor Marinho, Daniel Henrique, Guilherme Abe.
layout: cover
fonts:
  sans: 'Robot'
  serif: 'Robot Slab'
  mono: 'Fira Code'
---

<img src="https://raw.githubusercontent.com/viktormarinho/deco-apps/main/presence/logo.png" style="filter: invert()" width="" height=""/>

**Otimize a conversão do seu e-commerce com Gatilhos Emocionais de Social Proof
em Tempo Real**

---

<br>
<br>
<br>
<br>
<br>
<br>

<div style="display: flex; align-items: start; gap: 4rem; justify-content: center;">
  <div style="display: flex; align-items: center; flex-direction: column; gap: 1rem;">
    <div style="display: flex; align-items: end; gap: 1rem; margin-top: .5rem;">
      <img src="https://raw.githubusercontent.com/deco-cx/apps/main/decohub/logo.png" style="" width="150" height=""/>
      <svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-apps" width="48" height="48" viewBox="0 0 24 24" stroke-width="2" stroke="green" fill="none" stroke-linecap="round" stroke-linejoin="round">
        <path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
        <path d="M4 4m0 1a1 1 0 0 1 1 -1h4a1 1 0 0 1 1 1v4a1 1 0 0 1 -1 1h-4a1 1 0 0 1 -1 -1z"></path>
        <path d="M4 14m0 1a1 1 0 0 1 1 -1h4a1 1 0 0 1 1 1v4a1 1 0 0 1 -1 1h-4a1 1 0 0 1 -1 -1z"></path>
        <path d="M14 14m0 1a1 1 0 0 1 1 -1h4a1 1 0 0 1 1 1v4a1 1 0 0 1 -1 1h-4a1 1 0 0 1 -1 -1z"></path>
        <path d="M14 7l6 0"></path>
        <path d="M17 4l0 6"></path>
      </svg>
    </div>
<h5>Deco Apps</h5>
</div>
  <img src="https://raw.githubusercontent.com/viktormarinho/deco-apps/main/presence/logo.png" style="filter: invert()" width="" height=""/>
</div>

<br>
<br>
<br>

<h4 style="text-align: center;">
Plug and Play de Sections, Handlers e Actions para o seu site deco.cx
</h4>

---

## Instalação

1. Instale via decohub.
2. Crie um Bloco de Aplicativo Presence.

**O Presence está pronto para ser configurado.**

---

## Configuração

1. Configure o manipulador do Presence de acordo com suas necessidades.

Aqui está um exemplo de como você faria isso:

```ts
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

---

Para a configuração padrão, isso já é o suficiente! Se você deseja ir mais a
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

---

2. Agora você pode usar qualquer Seção do Presence, e elas usarão o manipulador
   do Presence para rastrear toda a lógica em tempo real necessária.

Por exemplo, se você deseja exibir a Seção PresenceCounter, que mostra um
contador de quantas pessoas estão na página atual (útil para gatilhos de Prova
Social), você pode usá-la assim:

```ts
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

---

O Fresh não permitirá que nenhum Aplicativo Deco externo crie uma Island, a
menos que você o reexporte explicitamente na pasta Islands, portanto, esta etapa
é necessária para que o componente funcione corretamente.

Isso é tudo sobre o PresenceCounter. Agora, quando você abrir o painel de Seções
em `admin.deco.cx`, você poderá adicionar o PresenceCounter a qualquer página e
configurá-lo por meio das Propriedades da Seção.
