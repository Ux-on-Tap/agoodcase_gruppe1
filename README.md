Teknisk dokumentation – [A Good Case]

Om projektet
Dette projekt er lavet som en del af Tema 9. Vi har lavet et dynamisk website med HTML, CSS og JavaScript, hvor indholdet bliver hentet fra et Rest API.

Vi har kodet dynamisk i Astro, hvor vi har brugt dynamic routes til at lave undersider, hvor sidens indhold bliver hentet som JSON fra Supabase. I Supsebase har vi oprettet vores datastruktur og API. Vi har kodet flere komponenter, herunder bl.a. productcard og anvendt slot elementer.

Sitet består af flere sider, hvor brugeren kan:

se categorier på forsiden
se en productliste med indhold
bruge filtrering eller sortering af produkter
klikke sig videre til en detaljeside
se data fra Supabase om produktet

Links
GitHub repository: [https://github.com/Ux-on-Tap/agoodcase_gruppe1]
Netlify: [https://agoodcasegruppe1.netlify.app/]
Figma: [https://www.figma.com/design/lqCcmfpasrrMwdNCvPAs4q/T9_team_1_AGC_Figma?node-id=506-2222&t=cZGcdqiC4zpSDkhK-1]
Figma Prototype: [https://www.figma.com/design/CUTXv5CAjY6iQUYu6Q8Qs6/team1_tema9?node-id=120-181&t=EwRfGoPIP76aNuPz-1]
Figma Slidedeck: [https://www.figma.com/deck/wflO1GVVCM6ZAKCa9imbkk/A-Good-Case_presentation?node-id=1-42]
Trello: [https://trello.com/b/BPOMmkdy/t9team1agoodcase]

Projektstruktur
Projektet er opdelt i Astro Pages, Layout, CSS og Components.

project/
├── index.astro
├── shop.astro
├── detaljer.astro
│ └──[id].astro
├── erhverv.astro
├── events.astro
├── omos.astro
├── css/
│ └── geneal.css
│ └── custom.css
├── layouts/
│ ├── layout.astro
└── README.md

Filbeskrivelser
Layout.astro implementerer vores html-skelet på astro pages

index.astro – Bruges til forsiden. Her bliver indhold vist dynamisk, fx kategorier.
shop.astro – Henter data fra Supabase og viser en liste med produkterne på siden.
detaljer.astro – Viser detaljer om et valgt produkt

CSS-filerne – styrer designet

Astro-filerne – styrer det dynamiske indhold på de forskellige sider vha. JavaScript i fence

<!-- er i tvivl nedenfor ift. astro og JS -->

Hvordan koden fungerer
Vi har opdelt Astro (Js), så hver side har sin egen fil.

Flow:

Siden loader

<!-- assist fra C? -->

JavaScript/Astro kører
Data hentes fra Rest API
Data bliver gennemgået med loop
HTML bliver indsat i DOM'en
Brugeren kan klikke på et produkt
detaljer.astro bruges til detaljesiden. Den læser et id fra URL'en og henter derefter den rigtige data fra Supabase.

Det gør det muligt at genbruge den samme HTML-opsætning til alle produkterne. I stedet for at lave én side per produkt, bruger vi ét id i URL'en til at vise det rigtige indhold.

Navngivning
Vi har navngivet vores filer, variabler, funktioner og komponenter så de, så tydeligt som muligt, er selvforklarende.

<!-- nået hertil -->

Eksempler på variabler
const recipeContainer;
const recipeId;
const selectedCategory;

<!-- const title = Astro.props.title;
const variant = Astro.props.variant; -->

Eksempler på funktioner
fetchRecipes();
showRecipes();
showRecipeDetails();
validateForm();

<!-- den her eller....
const endpoint =
  "https://phmyuxewmvhrkzgmjrtw.supabase.co/rest/v1/Datastruktur_produkter?limit=4";

const options = {
  headers: { apikey: "sb_publishable_vji-RnXHn3KkTNJ4KqYoxA_HzS1mbaj" },
};

const data = await fetch(endpoint, options).then((response) => response.json()); -->

<!-- ....den her?
 {data.map((product) => <ProductDetails {product} />)}
  {data.map((product) => <Cardrigtig {product} />)}-->

Vi har brugt camelCase i JavaScript, fordi det gør koden mere ensartet og lettere at læse.

Kommentarer i koden
Vi har kommenteret de steder i koden, hvor det giver mening. Fx ved funktioner, fetch-kald og steder hvor der sker DOM-manipulation.

Eksempel:

// Henter opskrifter fra Rest API'et
async function fetchRecipes() {
const res = await fetch(apiURL);
const data = await res.json();
return data.recipes;
}
Vi har prøvet ikke at skrive kommentarer til helt åbenlyse ting, men kun dér hvor det hjælper forståelsen.

Data og JSON-struktur
Vi henter data fra et API i JSON-format.

Et objekt kan fx se sådan ud:

{
"id": 1,
"title": "Opskriftsnavn",
"description": "Kort beskrivelse",
"category": "dessert",
"cookTime": 45,
"servings": 4,
"thumbnail": "billede.jpg"
}
Felter vi bruger
id – bruges til at sende brugeren videre til detaljesiden
title – opskriftsnavn
description – beskrivelse af opskriften
category – opskriftkategori (fx dessert, hovedret, forret)
cookTime – tilberedningstid i minutter
servings – antal portioner
thumbnail – opskriftsbillede
Formular og validering
Vi har lavet en formular, hvor brugeren kan indtaste oplysninger.

HTML-validering:

required – feltet skal udfyldes
type="email" – validerer email-format
type="number" – accepterer kun tal
Det sikrer, at brugeren ikke kan sende formularen, hvis felterne ikke er udfyldt korrekt.

Git og branches
Vi har brugt GitHub til at samarbejde om projektet.

Vi har arbejdet med branches, så vi ikke sad og ændrede i det samme på samme tid.

Vi navngav branchene med feature først og navnet på den, der lavede branchen til sidst.

Eksempler på branches
feature-forside-steen
feature-opskriftsliste-peter
feature-detaljeside-karsten
feature-formular-pia
Workflow
Lave en branch med feature-navn og eget navn til sidst
Kode en feature
Committe ændringer
Pushe til GitHub
Merge til main når det virkede
Det gjorde det nemmere at holde styr på, hvem der lavede hvad.

Bæredygtighed
Vi har tænkt bæredygtighed ind i projektet ved at holde page weight under 250 kb samt en enkel informationasarkitektur.

Tiltag:

Ingen videoer
Ingen tunge frameworks
Genbruge af kode
Optimerede billeder
Udfordringer undervejs
En af vores udfordringer var at få data fra Rest API’et vist korrekt på siderne. Det var også lidt svært at få id med videre i URL’en til detaljesiden.

Løsninger:

Console.logge data undervejs
Teste fetch-kald separat
Bruge URLSearchParams
Dele opgaverne mere tydeligt i gruppen
Mulige forbedringer
Hvis vi skulle arbejde videre med projektet, kunne vi forbedre det ved at tilføje:

Søgefunktion
Error handling
Loading state

Gruppemedlemmer
Camille Elleholm
Oliver Hartmann
Annebeth Fauerby
Te Rahbæk
