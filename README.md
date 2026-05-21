# 💰 Gastos Familia

App web para administrar los gastos familiares en tiempo real.
Todos ven los mismos datos desde su celular o computadora.

---

## 🚀 Cómo poner esto a funcionar (15 min)

### Paso 1 — Crear base de datos gratis en Supabase

1. Entra a [supabase.com](https://supabase.com) e inicia sesión con GitHub
2. Crea un **New Project** (nombre: `gastos-familia`, región: South America)
3. Ve al **SQL Editor** y ejecuta este código:

```sql
create table gastos (
  id bigint generated always as identity primary key,
  fecha date not null,
  monto numeric(10,2) not null,
  categoria text not null,
  quien text not null,
  descripcion text not null,
  created_at timestamptz default now()
);

alter table gastos enable row level security;
create policy "acceso_publico" on gastos for all using (true) with check (true);
```

4. Ve a **Project Settings → API** y copia:
   - **Project URL** (algo como `https://xxxx.supabase.co`)
   - **anon public key** (la llave larga)

---

### Paso 2 — Configurar el proyecto

Abre el archivo `config.js` y pega tus credenciales:

```js
const SUPABASE_URL = 'https://TU_URL.supabase.co';   // ← pega aquí
const SUPABASE_KEY = 'TU_ANON_KEY_AQUI';              // ← pega aquí
```

---

### Paso 3 — Subir a GitHub

1. Crea un repositorio nuevo en [github.com](https://github.com) (nombre: `gastos-familia`)
2. Sube los archivos `index.html` y `config.js`

---

### Paso 4 — Publicar gratis en Vercel

1. Entra a [vercel.com](https://vercel.com) con tu cuenta de GitHub
2. Click en **Add New → Project**
3. Selecciona el repositorio `gastos-familia`
4. Click **Deploy** — ¡listo!

Vercel te da un link tipo `gastos-familia.vercel.app`.  
**Comparte ese link con tu familia por WhatsApp y ya todos pueden usarlo.**

---

## 📱 ¿Cómo lo usan?

- Entran al link desde su celular
- Agregan gastos con fecha, monto, categoría y quién pagó
- En la pestaña **Gráficas** ven en qué gastan más
- En **Historial** pueden filtrar por persona o mes
- Cualquiera puede exportar a Excel con un botón

---

## 🛠 Archivos del proyecto

```
gastos-familia/
├── index.html   ← toda la app
└── config.js    ← tus credenciales de Supabase
```
