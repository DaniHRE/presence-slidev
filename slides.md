---
title: Presence
author: Viktor Marinho, Daniel Henrique, Guilherme Abe.
layout: cover
transition: fade
fonts:
  sans: Robot
  serif: Robot Slab
  mono: Fira Code
---

<img v-click src="presence-old.png" style="filter: invert()" width="300" height=""/>

<h4 v-after style="position: absolute; bottom: 2rem; left: 2rem;">
Viktor Marinho
</h4>


---
layout: center
---

<img src="counter.gif" width="600" style="border-radius: 8px; filter: drop-shadow(5px 5px 10px white);" />

---
layout: center
transition: slide-left
---

<img src="presence-old.png" style="margin: auto; filter: invert();" width="500" height=""/>

---
layout: center
---

<div style="display: flex; align-items: center; margin-bottom: 150px;">
  <img src="presence-new.png" style="margin: auto; filter: invert();" width="500" height=""/>
  <img src="bolt.svg" class="bolt" style="margin-top: 20px;"/>
</div>

<h3 v-click="1" style="text-align: center; margin-top: -150px;">
Redefinir experiências
</h3>

<h3 v-click="2" style="text-align: center;">
Taxas de Conversão de 6 a 10 vezes maiores
</h3>

<h3 v-click="3" style="text-align: center;">
10% do mercado de varejo Chinês
</h3>

---
layout: center
---

<h1 style="text-align: center; margin-top: 0">Live Commerce</h1>

<div style="display: flex; align-items:center; gap: 4rem">
  <div v-click="1" style="display: flex; align-items:center; flex-direction: column;">
  <img src="connections.gif" width="200" style=" border-radius: 8px"/>
  <h5 style="text-align: center;">Conexões genuínas <br> entre Consumidor e marca</h5>
  </div>
  <div v-click="2" style="display: flex; align-items:center; flex-direction: column;">
  <img src="review.gif" width="300" style=" border-radius: 8px;"/>
  <h5 style="text-align: center;">Melhor visão do produto, <br> com experiência mais envolvente</h5>
  </div>
</div>

<div style="display: flex; align-items: center; position: absolute; bottom: 2rem; right: 2rem;">
  <img src="presence-new.png" style="margin: auto; filter: invert();" width="150" height=""/>
  <img src="bolt.svg" class="bolt" style="height: 40px;"/>
</div>

---
layout: center
---

<div style="display: flex; align-items: center; gap: 4rem; justify-content: center; margin-left: 4.5rem;">
  <div style="display: flex; align-items: center; flex-direction: column; gap: 1rem;">
    <div style="display: flex; align-items: end; gap: 1rem;">
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
  <span>🤝</span>
  <div style="display: flex; align-items: center;margin-bottom: 35px;">
    <img src="presence-new.png" style="margin: auto; filter: invert();" width="250" height=""/>
    <img src="bolt.svg" class="bolt" style="margin-top: 5px; width: 70px;"/>
  </div>
</div>

<h4 style="position: absolute; bottom: 2rem; left: 2rem;">
Daniel Henrique
</h4>

---
layout: center
---

<img src="stream-architecture.png" width="400" style="border-radius: 8px; margin: auto" />
<br>
<h4 style="text-align: center;">Exemplo de arquitetura de <br> um serviço de streaming de vídeo</h4>


<div style="display: flex; align-items: center; position: absolute; bottom: 2rem; right: 2rem;">
  <img src="presence-new.png" style="margin: auto; filter: invert();" width="150" height=""/>
  <img src="bolt.svg" class="bolt" style="height: 40px;"/>
</div>

---
layout: center
---

<img src="chat.gif" width="600" style="border-radius: 8px; filter: drop-shadow(5px 5px 10px white);" />

<div style="display: flex; align-items: center; position: absolute; bottom: 2rem; right: 2rem;">
  <img src="presence-new.png" style="margin: auto; filter: invert();" width="150" height=""/>
  <img src="bolt.svg" class="bolt" style="height: 40px;"/>
</div>

---
layout: center
---

`routes/presence/index.ts`

```ts
import { createPresenceHandler } from "apps/presence/infra/presenceRoom.ts";

export const handler = createPresenceHandler({});
```


<div style="display: flex; align-items: center; position: absolute; bottom: 2rem; right: 2rem;">
  <img src="presence-new.png" style="margin: auto; filter: invert();" width="150" height=""/>
  <img src="bolt.svg" class="bolt" style="height: 40px;"/>
</div>

---
layout: center
---

`routes/presence/index.ts`

```ts
import { createPresenceHandler } from "apps/presence/infra/presenceRoom.ts";

export const handler = createPresenceHandler({
  onError: (err) => externalLogService.error(err),
  onRoomStateChange: (room) => {
    otherRealtimeService.notifyStateChange(room.connections);
  }
});
```

É possível "hookar" em eventos relevantes para extender a funcionalidade

<div style="display: flex; align-items: center; position: absolute; bottom: 2rem; right: 2rem;">
  <img src="presence-new.png" style="margin: auto; filter: invert();" width="150" height=""/>
  <img src="bolt.svg" class="bolt" style="height: 40px;"/>
</div>

---
layout: center
---

<img src="pagespeed.png" width="450" style="border-radius: 8px;"/>
<h4 style="margin-top: 1rem; text-align: center;">Zero peer-dependencies + Bundle mínimo</h4>

<div style="display: flex; align-items: center; position: absolute; bottom: 2rem; right: 2rem;">
  <img src="presence-new.png" style="margin: auto; filter: invert();" width="150" height=""/>
  <img src="bolt.svg" class="bolt" style="height: 40px;"/>
</div>

---
layout: center
---

<div style="text-align: center;">
<h3>
  <svg style="display: inline;" xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-brand-github" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
    <path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
    <path d="M9 19c-4.3 1.4 -4.3 -2.5 -6 -3m12 5v-3.5c0 -1 .1 -1.4 -.5 -2c2.8 -.3 5.5 -1.4 5.5 -6a4.6 4.6 0 0 0 -1.3 -3.2a4.2 4.2 0 0 0 -.1 -3.2s-1.1 -.3 -3.5 1.3a12.3 12.3 0 0 0 -6.2 0c-2.4 -1.6 -3.5 -1.3 -3.5 -1.3a4.2 4.2 0 0 0 -.1 3.2a4.6 4.6 0 0 0 -1.3 3.2c0 4.6 2.7 5.7 5.5 6c-.6 .6 -.6 1.2 -.5 2v3.5"></path>
  </svg> 
  <span>deco-cx/apps</span>
</h3>
<h3 style="text-decoration: underline; color: dodgerblue;">Pull request #188</h3>
</div>

<div style="display: flex; align-items: center; position: absolute; bottom: 2rem; right: 2rem;">
  <img src="presence-new.png" style="margin: auto; filter: invert();" width="150" height=""/>
  <img src="bolt.svg" class="bolt" style="height: 40px;"/>
</div>

---
layout: center
---

## Obrigado pela atenção!

<br>
  <div style="display: flex; align-items: center;margin-bottom: 35px;">
    <img src="presence-new.png" style="margin: auto; filter: invert();" width="250" height=""/>
    <img src="bolt.svg" class="bolt" style="margin-top: 5px; width: 70px;"/>
  </div>
---
