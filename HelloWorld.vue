<template>
  <div>
    <!-- 1. Template Syntax -->
    <p>{{ message }}</p> <!-- a. Text Interpolation -->
    <p v-html="rawHtml"></p> <!-- b. Raw HTML -->
    <div :id="dynamicId"></div> <!-- c. Attribute Bindings -->
    <p>{{ 2 + 3 }}</p> <!-- d. JavaScript expressions inside syntax -->

    <!-- 2. Methods -->
    <button @click="sayHello">Click me</button>

    <!-- 3. Reactivity Fundamentals -->
    <p>{{ reactiveData }}</p>

    <!-- 4. Computed Properties -->
    <p>{{ computedProperty }}</p>

    <!-- 5. Class and Style Bindings -->
    <div :class="{'active': isActive}" :style="{ color: textColor }"></div>

    <!-- 6. List Rendering -->
    <template>
      <ul>
      <template v-for="(item, index) in tasks">
        <li :key="index" v-if="item.visible">{{ item.name }}</li>
      </template>
      </ul>
    </template>


    <!-- 7. Event Handling: Listening to Events -->
    <button @click="inlineHandler">Inline Handler</button> <!-- a. Inline Handlers -->
    <button @click="methodHandler">Method Handler</button> <!-- b. Method Handlers -->

    <!-- 8. Form Input Bindings -->
    <input type="text" v-model="textModel" />
    <input type="checkbox" v-model="isChecked" />
    <input type="radio" v-model="selectedRadio" :value="1" />
    <select v-model="selectedOption">
      <option value="option1">Option 1</option>
      <option value="option2">Option 2</option>
    </select>
    <textarea v-model="textareaModel"></textarea>

    <!-- 9. Watchers -->
    <p>{{ watchedValue }}</p>

    <!-- 10. Components -->
    <child-component :prop1="parentData" @customEvent="handleCustomEvent">
      <template v-slot:default>
        <!-- Content for slot -->
      </template>
    </child-component>

    <!-- 11. Router -->
    <router-link to="/page">Go to Page</router-link>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  data() {
    return {
      message: 'Hello, Vue!',
      rawHtml: '<span style="color: red;">Red Text</span>',
      dynamicId: 'elementId',
      reactiveData: ref('Reactive Data'),
      list: ['Item 1', 'Item 2', 'Item 3'],
      isActive: true,
      textColor: 'blue',
      items: [{ id: 1, text: 'Item 1' }, { id: 2, text: 'Item 2' }],
      textModel: '',
      isChecked: false,
      selectedRadio: 1,
      selectedOption: 'option1',
      textareaModel: '',
      watchedValue: '',
      parentData: 'Data from Parent',
    };
  },
  computed: {
    computedProperty() {
      return 'Computed Property';
    },
  },
  methods: {
    sayHello() {
      alert('Hello!');
    },
    inlineHandler() {
      console.log('Inline Handler');
    },
    methodHandler() {
      console.log('Method Handler');
    },
    handleCustomEvent(data) {
      console.log('Received custom event with data:', data);
    },
  },
  watch: {
    watchedValue(newValue, oldValue) {
      console.log(`Watched Value changed from ${oldValue} to ${newValue}`);
    },
  },
};
</script>

<style scoped>
/* Base styles */
body {
  font-family: Arial, sans-serif;
  margin: 2rem;
  background-color: #f9f9f9;
}

/* Make the div containing everything have a card look */
div {
  padding: 2rem;
  background-color: #fff;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
}

/* Styling for buttons */
button {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  background-color: #007BFF;
  color: white;
  margin: 0.5rem 0;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #0056b3;
}

/* Styling for form elements */
input[type="text"], textarea, select {
  width: 100%;
  padding: 0.5rem;
  margin: 0.5rem 0;
  border: 1px solid #ddd;
  border-radius: 4px;
}

input[type="checkbox"], input[type="radio"] {
  margin-right: 0.5rem;
}

/* Styling for list items */
ul {
  list-style-type: none;
  padding: 0;
}

li {
  background-color: #e9e9e9;
  padding: 0.5rem;
  margin: 0.2rem 0;
  border-radius: 4px;
}

/* Styling for router links */
router-link {
  text-decoration: none;
  color: #007BFF;
  padding: 0.5rem;
  border: 1px solid #007BFF;
  border-radius: 4px;
  display: inline-block;
  transition: background-color 0.3s;
}

router-link:hover {
  background-color: #007BFF;
  color: white;
}

/* Conditional class for active items */
.active {
  background-color: #007BFF;
  color: white;
}
</style>

