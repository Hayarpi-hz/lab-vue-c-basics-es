<script setup>
import { ref } from "vue";

function generateId() {
  return Math.random().toString(36).substr(2, 9);
}

const name = ref("");

const generateMessage = () => {
  return `Hola, ${name.value}`;
};

const isOpen = true;

const bookLibrary = [
  {
    id: generateId(),
    title: "El Principito",
    description:
      "Una historia sobre un joven príncipe que explora planetas lejanos.",
    author: {
      id: generateId(),
      name: "Antoine de Saint-Exupéry",
    },
    content:
      "Había una vez un pequeño príncipe que vivía en un planeta muy lejano...",
  },
  {
    id: generateId(),
    title: "Cien años de soledad",
    description: "Una saga sobre la familia Buendía en el pueblo de Macondo.",
    author: {
      id: generateId(),
      name: "Gabriel García Márquez",
    },
    content:
      "Muchos años después, frente al pelotón de fusilamiento, el coronel Aureliano Buendía había de recordar aquella tarde remota en que su padre lo llevó a conocer el hielo...",
  },
  {
    id: generateId(),
    title: "1984",
    description: "Una novela distópica sobre un régimen totalitario.",
    author: {
      id: generateId(),
      name: "George Orwell",
    },
    content: "Era un día frío y luminoso de abril y el reloj daba las trece...",
  },
  {
    id: generateId(),
    title: "Orgullo y prejuicio",
    description:
      "Una historia sobre el amor y las costumbres sociales en el siglo XIX.",
    author: {
      id: generateId(),
      name: "Jane Austen",
    },
    content:
      "Es una verdad mundialmente aceptada que un hombre soltero, poseedor de una gran fortuna, necesita una esposa...",
  },
  {
    id: generateId(),
    title: "La Odisea",
    description: "Las aventuras de Odiseo en su viaje de regreso a Ítaca.",
    author: {
      id: generateId(),
      name: "Homero",
    },
    content:
      "Dímelo, oh Musa, las múltiples hazañas de aquel varón ingenioso que anduvo errante tras saquear la ciudad sagrada de Troya...",
  },
  {
    id: generateId(),
    title: "El Gran Gatsby",
    description:
      "La historia de Jay Gatsby y su obsesión con la riqueza y el amor.",
    author: {
      id: generateId(),
      name: "F. Scott Fitzgerald",
    },
    content:
      "En mi primer año en Nueva York había algo indescriptiblemente emocionante sobre las noches de verano en la ciudad...",
  },
];

const colors = ['lightblue', 'lightgreen', 'lightcoral', 'lightgoldenrodyellow', 'lightpink', 'lightsalmon', 'lightseagreen', 'lightskyblue'];

const bgColor = ref("white");
const toggleColor = () => {
  const randomIndex = Math.floor(Math.random() * colors.length);
  bgColor.value = colors[randomIndex];
};
</script>

<template>
  <div>
    <div :style="{ backgroundColor: bgColor }" class="color-box">
      <button @click="toggleColor">Cambiar el color de fondo</button>
    </div>
    <h1>Libros</h1>
    El resultado de 2 + 2 es: {{ 2 + 2 }}
    <p>{{ generateMessage() }}</p>
    <p v-if="isOpen">Bienvenido a mi librería</p>
    <p v-else>Ahora vuelvo</p>
    <h2>Mejores títulos</h2>
    <ul>
      <li v-for="book in bookLibrary" :key="book.id">
        <h3>{{ book.title }}</h3>
        <i>{{ book.description }}</i>
        <p>{{ book.content }}</p>
      </li>
    </ul>
  </div>
</template>

<style>
.color-box {
  width: 300px;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 2px solid black;
}
</style>
