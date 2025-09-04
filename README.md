# - Transitions : `transition-property`, `transition-duration`, `timing-function`.

🔹 Définition formelle

Une transition CSS est un effet qui contrôle la vitesse du changement d’une ou plusieurs propriétés CSS, lorsqu’un élément passe d’un état à un autre (par ex. normal → :hover, non coché → :checked, non focus → :focus).
 [Les exemples en ligne](https://lokonon52.github.io/CSS/7-Transition/)
## Les 3 propriétés fondamentales des transitions CSS sont :

- `transition-property`
- `transition-duration`
- `transition-timing-function`

Et je vais aussi donner leur **équivalence en Tailwind CSS** avec des exemples clairs ✅

---

## 1. `transition-property`

👉 Définit **quelle propriété CSS** va être animée lors d’un changement d’état (ex: `hover`, `focus`…).

### Syntaxe CSS

```css
transition-property: background-color, transform;
```

Ici, seules les propriétés `background-color` et `transform` seront animées.

### Exemple CSS

```css
button {
  transition-property: background-color, transform;
  transition-duration: 0.3s;
}

button:hover {
  background-color: red;
  transform: scale(1.1);
}
```

### Équivalence Tailwind

- `transition-none` → aucune propriété
- `transition-all` → toutes les propriétés animables
- `transition-colors` → couleurs (background, border, text…)
- `transition-opacity` → opacité
- `transition-shadow` → ombres
- `transition-transform` → transformations (`scale`, `rotate`, `translate`, etc.)

```html
<button
  class="transition-colors transition-transform duration-300 hover:bg-red-500 hover:scale-110"
>
  Bouton animé
</button>
```

---

## 2. `transition-duration`

👉 Définit **la durée de la transition**.

### Syntaxe CSS

```css
transition-duration: 500ms;
```

### Exemple CSS

```css
div {
  transition-property: opacity;
  transition-duration: 1s;
}

div:hover {
  opacity: 0.5;
}
```

### Équivalence Tailwind

- `duration-75` → `75ms`
- `duration-100` → `100ms`
- `duration-150` → `150ms`
- `duration-200` → `200ms`
- `duration-300` → `300ms`
- `duration-500` → `500ms`
- `duration-700` → `700ms`
- `duration-1000` → `1000ms (1s)`

```html
<div class="transition-opacity duration-700 hover:opacity-50">
  Texte avec transition lente
</div>
```

---

## 3. `transition-timing-function`

👉 Définit **la vitesse de progression** de l’animation (accélération, ralenti, linéaire…).

### Syntaxe CSS

```css
transition-timing-function: ease-in-out;
```

### Valeurs principales CSS

- `ease` → valeur par défaut (démarre lentement, accélère, puis ralentit)
- `linear` → vitesse constante
- `ease-in` → démarre lentement puis accélère
- `ease-out` → démarre vite puis ralentit
- `ease-in-out` → lent au début et à la fin

### Exemple CSS

```css
img {
  transition: transform 0.5s ease-in-out;
}

img:hover {
  transform: rotate(10deg);
}
```

### Équivalence Tailwind

- `ease-linear` → `linear`
- `ease-in` → `ease-in`
- `ease-out` → `ease-out`
- `ease-in-out` → `ease-in-out`

```html
<img
  class="transition-transform duration-500 ease-in-out hover:rotate-6"
  src="image.jpg"
/>
```

---

## 🎯 Résumé en tableau

| Propriété CSS                | Rôle                                  | Équivalence Tailwind                                                                                                        |
| ---------------------------- | ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| `transition-property`        | Quelle propriété est animée           | `transition-none`, `transition-all`, `transition-colors`, `transition-opacity`, `transition-shadow`, `transition-transform` |
| `transition-duration`        | Durée de l’animation                  | `duration-75`, `duration-100`, `duration-150`, … `duration-1000`                                                            |
| `transition-timing-function` | Vitesse de progression de l’animation | `ease-linear`, `ease-in`, `ease-out`, `ease-in-out`                                                                         |

---

Super 👍 Excellente idée !
Je vais te montrer **3 exemples complets** avec le code **en CSS pur** et son équivalent **en Tailwind CSS**, côte à côte.

---

## 🔹 Exemple 1 : Bouton avec changement de couleur et zoom

### 🎨 CSS classique

```css
button {
  background-color: blue;
  color: white;
  padding: 10px 20px;
  border-radius: 8px;
  transition-property: background-color, transform;
  transition-duration: 300ms;
  transition-timing-function: ease-in-out;
}

button:hover {
  background-color: red;
  transform: scale(1.1);
}
```

### 🌀 Tailwind CSS

```html
<button
  class="bg-blue-500 text-white px-4 py-2 rounded-lg 
               transition-colors transition-transform 
               duration-300 ease-in-out 
               hover:bg-red-500 hover:scale-110"
>
  Bouton animé
</button>
```

---

## 🔹 Exemple 2 : Image qui tourne au survol

### 🎨 CSS classique

```css
img {
  width: 200px;
  transition-property: transform;
  transition-duration: 500ms;
  transition-timing-function: ease-in;
}

img:hover {
  transform: rotate(15deg);
}
```

### 🌀 Tailwind CSS

```html
<img
  src="photo.jpg"
  class="w-52 transition-transform duration-500 ease-in hover:rotate-12"
/>
```

---

## 🔹 Exemple 3 : Bloc qui change d’opacité

### 🎨 CSS classique

```css
.box {
  background-color: teal;
  width: 150px;
  height: 150px;
  transition-property: opacity;
  transition-duration: 1000ms;
  transition-timing-function: ease-out;
}

.box:hover {
  opacity: 0.5;
}
```

### 🌀 Tailwind CSS

```html
<div
  class="bg-teal-500 w-36 h-36 
            transition-opacity duration-1000 ease-out 
            hover:opacity-50"
></div>
```

Parfait 👍 tu veux documenter ton **Exemple 4** directement dans un `README.md`.
Je vais te préparer une section bien structurée avec ton code CSS **et** son équivalent **TailwindCSS** côte à côte.

---

## 🔹 Exemple 4: Transition avec `background-image: linear-gradient()` et `background-position`

Cet exemple montre comment animer le **déplacement d’un dégradé linéaire** sur un cercle au survol.

---

### 🔹 Version CSS classique

```css
.circle {
  font-size: 34px;
  width: 100px;
  height: 100px;
  background-color: black;
  background-repeat: no-repeat;
  border-radius: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  color: azure;
  background-position: -45px 0;
  transition-property: background-position;
  transition-duration: 0.5s;
  transition-timing-function: ease-in;
}

.circle:hover {
  background-position: 0 0;
  background-image: linear-gradient(#ff4648, #ff4648);
}
```

**HTML :**

```html
<div class="circle">A</div>
```

---

### 🔹 Version Tailwind CSS

```html
<div
  class="w-[100px] h-[100px] rounded-full 
            flex justify-center items-center 
            text-[34px] text-azure 
            bg-black bg-no-repeat 
            bg-[position:-45px_0] 
            transition-[background-position] duration-500 ease-in
            hover:bg-[linear-gradient(#ff4648,#ff4648)] hover:bg-[position:0_0]"
></div>
```

---

### 📝 Explications

- `bg-[position:-45px_0]` → définit la position initiale du background
- `transition-[background-position]` → anime uniquement le déplacement du background
- `hover:bg-[linear-gradient(...)]` → applique un dégradé rouge au survol
- `hover:bg-[position:0_0]` → déplace le dégradé pour remplir le cercle

👉 Résultat : au survol, le cercle passe progressivement **du noir vers le rouge dégradé**.

--

✅ Dans chaque cas, tu vois que **les 3 propriétés CSS** :

- `transition-property`
- `transition-duration`
- `transition-timing-function`

sont traduites directement en **classes utilitaires Tailwind**.

---
Exactement ✅ !
On peut combiner **`:focus`** et **`:checked`** avec **`transition`** pour rendre les changements plus fluides (bordures, couleurs, ombres, etc.).

---

 ## 🔹 Exemple 5  `:focus` + `transition`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Focus + Transition</title>
  <style>
    input[type="text"] {
      padding: 8px;
      border: 2px solid gray;
      border-radius: 5px;
      outline: none;
      transition: all 0.3s ease; /* transition fluide */
    }

    input[type="text"]:focus {
      border-color: royalblue;
      box-shadow: 0 0 10px royalblue;
    }
  </style>
</head>
<body>
  <h2>:focus avec transition</h2>
  <input type="text" placeholder="Clique ici">
</body>
</html>
```

👉 Quand tu cliques, la bordure et l’ombre passent **progressivement** au bleu.

---

## 🔹 Exemple 6 avec `:checked` + `transition`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Checked + Transition</title>
  <style>
    input[type="checkbox"] {
      width: 20px;
      height: 20px;
      cursor: pointer;
      appearance: none; /* on cache le style par défaut */
      border: 2px solid gray;
      border-radius: 4px;
      transition: all 0.3s ease; /* transition fluide */
    }

    input[type="checkbox"]:checked {
      background-color: limegreen;
      border-color: limegreen;
    }
  </style>
</head>
<body>
  <h2>:checked avec transition</h2>
  <label>
    <input type="checkbox"> Accepter
  </label>
</body>
</html>
```

👉 Ici, la case passe **doucement** de vide → verte quand on coche.

---

## 3. Version **Tailwind**

Avec Tailwind, on ajoute simplement `transition` + `duration-*` + `ease-*`.

```html
<!-- Input texte avec :focus -->
<input type="text" placeholder="Clique ici"
  class="p-2 border-2 border-gray-400 rounded outline-none 
         focus:border-blue-500 focus:ring-2 focus:ring-blue-500 
         transition duration-300 ease-in-out">

<!-- Checkbox avec :checked -->
<label class="flex items-center space-x-2">
  <input type="checkbox"
    class="w-5 h-5 border-2 border-gray-400 rounded cursor-pointer 
           transition duration-300 ease-in-out
           checked:bg-green-500 checked:border-green-500">
  <span>Accepter</span>
</label>
```

👉 Avec Tailwind, `checked:bg-*` et `checked:border-*` s’appliquent **quand la case est cochée**, et la `transition` rend ça fluide.

---


