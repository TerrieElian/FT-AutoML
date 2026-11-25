# Vingerquiz

Een quiz die je met je vingers beantwoordt: 1 vinger = A, 2 = B, 3 = C, 4 = D. De webcam leest je gebaar, een Teachable Machine-model herkent het in de browser (TensorFlow.js).

## Track

AutoML (Future Technologies, lab 04): een beeldclassificatiemodel getraind met Google Teachable Machine, gebruikt in een eigen webapp.

## Hoe starten

De camera werkt enkel op `localhost` of via HTTPS, dus open het bestand niet gewoon dubbelklikkend.

```bash
python3 -m http.server 8000
```

Open daarna http://localhost:8000/index.html, vul een naam in, klik **Start** en geef cameratoegang.

- Houd je gebaar ongeveer 1 seconde stil. De balk onder de antwoorden loopt dan vol.
- Na elke nieuwe vraag is er 2,5 seconden pauze waarin gebaren niet meetellen.
- Zonder camera werkt de quiz ook: klik op een antwoord of druk op toets 1 tot 4.
- Scores worden lokaal in de browser bewaard. Optioneel kan Supabase gebruikt worden (zie de commentaar bovenaan `index.html`).

Online zetten kan via GitHub Pages of Netlify (HTTPS is nodig voor de camera).

## Hoe de dataset gemaakt is

- Gemaakt met [Teachable Machine](https://teachablemachine.withgoogle.com/) (Image Project, Standard image model), met opnames via de webcam.
- 5 klassen: `Geen antwoord` (geen hand of neutrale houding), `A` (1 vinger), `B` (2 vingers), `C` (3 vingers), `D` (4 vingers).
- TODO: vul aan hoeveel opnames per klas, welke variatie (achtergrond, licht, linker- en rechterhand, afstand) en de gebruikte trainingsinstellingen (epochs, batch size, learning rate).
- Het getrainde model staat online: `https://teachablemachine.withgoogle.com/models/lH6D405it/` (ingesteld als `MODEL_URL` in `index.html`).

## Bestanden

- `index.html`: de hele app (quiz, camera, modelherkenning, scorebord).
