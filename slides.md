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

**Otimize a conversão do seu e-commerce com Gatilhos Emocionais de Social Proof em Tempo Real**

Plug and Play de Sections, Handlers e Actions para o seu site deco.cx.


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
import { createPresenceHandler } from "apps/presence/infra/presenceRoom.ts"

export const handler = createPresenceHandler({});
```

---

Para a configuração padrão, isso já é o suficiente!
Se você deseja ir mais a fundo, o Presence permite que você se conecte a alguns eventos, como
quando ocorre um erro (útil para registro e métricas),
ou quando o servidor WebSocket transmite mensagens para uma sala (útil para estender o comportamento).

Aqui está um exemplo mais complexo:

```ts
export const handler = createPresenceHandler({
    onError: (e) => {
        someLogService.registerError(e);
    },
    onRoomStateChange: (room) => {
        otherRealtimeService.notifyStateChange(room.connections);
    }
});
```

---

2. Agora você pode usar qualquer Seção do Presence, e elas usarão o manipulador do Presence para rastrear toda a lógica em tempo real necessária.

Por exemplo, se você deseja exibir a Seção PresenceCounter,
que mostra um contador de quantas pessoas estão na página atual (útil para gatilhos de Prova Social),
você pode usá-la assim:

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

O Fresh não permitirá que nenhum Aplicativo Deco externo crie uma Island, a menos que você o reexporte explicitamente na pasta Islands, portanto, esta etapa é necessária para que o componente funcione corretamente.

Isso é tudo sobre o PresenceCounter. Agora, quando você abrir o painel de Seções em `admin.deco.cx`,
você poderá adicionar o PresenceCounter a qualquer página e configurá-lo por meio das Propriedades da Seção.
