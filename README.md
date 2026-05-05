# Tipster — plataforma de pronósticos deportivos

Prototipo visual y funcional. Todo vive en `preview.html`.

## Cómo abrirlo

Doble clic en `preview.html` y se abre en el navegador. No necesita instalación.

## Credenciales

- **Admin**: las que tú me diste (escritas en el `<script>` de `preview.html`).
- **Cliente demo**: cualquier email de la base (p. ej. `carlos.m@gmail.com`) con contraseña `demo123`.

## Logos reales

Los logos están en la carpeta `RECURSOS/` que tú creaste. El preview los detecta automáticamente. Si un equipo o competición no tiene archivo, aparece la **píldora de color con siglas** como fallback.

### Conexión actual

He conectado el código a tu carpeta `RECURSOS/` usando los nombres exactos de tus archivos. La lista completa de equipos y competiciones disponibles en el formulario de "Nuevo pronóstico" es la siguiente.

### Equipos con logo conectado

**LaLiga (20)**: Real Madrid, Barcelona, Atlético de Madrid, Sevilla, Valencia, Athletic Club, Real Sociedad, Real Betis, Alavés, Celta de Vigo, Elche, Espanyol, Getafe, Girona, Levante, Mallorca, Osasuna, Rayo Vallecano, Real Oviedo, Villarreal.

**Premier League (20)**: Arsenal, Aston Villa, Bournemouth, Brentford, Brighton, Burnley, Chelsea, Crystal Palace, Everton, Fulham, Leeds, Liverpool, Manchester City, Manchester United, Newcastle, Nottingham Forest, Sunderland, Tottenham, West Ham, Wolves.

**Bundesliga (18)**: Augsburgo, Bayer Leverkusen, Bayern München, Borussia Dortmund, B. Mönchengladbach, Eintracht Frankfurt, Freiburg, Hamburgo, Heidenheim, Hoffenheim, Köln, Mainz 05, RB Leipzig, St. Pauli, Stuttgart, Union Berlin, Werder Bremen, Wolfsburg.

**Serie A (20)**: Atalanta, Bologna, Cagliari, Como, Cremonese, Fiorentina, Genoa, Hellas Verona, Inter de Milán, Juventus, Lazio, Lecce, AC Milan, Napoli, Parma, Pisa, Roma, Sassuolo, Torino, Udinese.

**Ligue 1 (18)**: Angers, Auxerre, Le Havre, Lille, Lorient, Lyon, Marseille, Metz, Monaco, Nantes, Niza, Paris FC, PSG, RC Lens, Estrasburgo, Rennes, Stade Brestois, Toulouse.

**Selecciones (5)**: España, Italia, Inglaterra, Francia, Alemania.

### Competiciones con logo conectado

- Champions League
- Europa League
- Conference League
- Mundial de Clubes
- Mundial 2026
- Copa del Rey
- Coppa Italia
- FA Cup

### Sin logo todavía (saldrán con píldora de color)

- **Ligas**: LaLiga, Premier League, Bundesliga, Serie A, Ligue 1.
- **Equipos sudamericanos**: Boca Juniors, River Plate, Flamengo, Palmeiras.
- **Tenis** (jugadores): Carlos Alcaraz, Jannik Sinner, Novak Djokovic, Alexander Zverev, Iga Swiatek, Aryna Sabalenka.
- **Tenis** (torneos): Roland Garros, Wimbledon, US Open, Australian Open, ATP Masters.
- **Baloncesto**: NBA, EuroLeague, Liga ACB, Lakers, Celtics, Bucks, Heat, Warriors.

Cuando tengas más archivos, los pones en `RECURSOS/` con el nombre exacto que aparece en el código (`slug`) y el preview los detecta solo. Si quieres añadir uno y no sabes qué nombre usar, dime el equipo/competición y te lo digo.

### ⚠️ Aviso legal

Los logos oficiales son **marca registrada**. Para uso comercial real necesitas licenciarlos (a través de la federación, club o un proveedor como SportRadar / API-Football).

## Estructura de carpetas

```
MB/
├── preview.html             ← archivo único con web + admin + cliente
├── README.md                ← este archivo
├── public/
│   ├── favicon.svg
│   └── logos/               ← carpetas vacías (puedes ignorarlas)
└── RECURSOS/                ← aquí están tus logos
    ├── realmadrid.png
    ├── barcelona.png
    ├── championsleague.png
    └── ... (más de 100 archivos)
```

## Aviso de seguridad sobre las credenciales admin

La contraseña del admin está escrita en el `<script>` de `preview.html`. **Cualquiera que vea el código fuente la puede leer.** Esto es **válido solo como prototipo**. Para producción hay que mover la autenticación a un servidor con contraseñas cifradas (NextAuth, Supabase Auth, etc.). Si subes esto a GitHub, marca el repositorio como **privado**.

## Persistencia de datos

Los pronósticos que crees, los cambios de estado/perfil de clientes y las apuestas seguidas se guardan automáticamente en `localStorage` del navegador. Esto significa que **persisten incluso si cierras el archivo y vuelves a abrirlo**, mientras uses el mismo navegador.

Lo único que NO persiste es el inicio de sesión (admin / cliente): por seguridad, al cerrar la pestaña tienes que volver a meter las credenciales.

### Restablecer datos

Para borrar todo y empezar de cero (clientes, pronósticos, apuestas seguidas), abre la consola del navegador (Cmd+Opt+J en Chrome / Cmd+Opt+I en Safari) y ejecuta:

```javascript
localStorage.clear(); sessionStorage.clear(); location.reload();
```

> ⚠️ Esto deja la base de clientes sin tus modificaciones (vuelve a los 12 originales) y borra los pronósticos creados.
