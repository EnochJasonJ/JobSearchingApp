<script setup>
import { ref , onMounted} from 'vue'

      const name = ref("Enoch Jason");
      const status = ref('active');
      const tasks = ref(['Task 1','Task 2','Task 3']);
      const newTask = ref('');

      const toggleStatus = () => {
        if(status.value === 'active'){
          status.value = 'pending';
        }
        else if(status.value === 'pending'){
          status.value = 'inactive';
        }
        else {
          status.value = 'active';
        }
      };

      const addTask = () => {
        if(newTask.value.trim !== ''){
          tasks.value.push(newTask.value);
          newTask.value = '';
        }
      };
      const deleteTask = (index) => {
        tasks.value.splice(index,1);
      };

      onMounted(async () => {
        try {
          const response = await fetch('https://jsonplaceholder.typicode.com/todos');
          const data = await response.json();
          tasks.value = data.map((task) => task.title);
        } catch (error) {
            console.log('Error fetching tasks');
        }
      });

</script>

<template>
  <h1> {{ name }} </h1>
  <p v-if="status === 'active'">{{ name }} is active</p>
  <p v-else-if="status === 'pending'">{{ name }} is pending</p>
  <p v-else>{{ name }} is inactive</p>
  <button @click="toggleStatus">Change Status</button>
  <form @submit.prevent="addTask">
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <button type="submit">Submit</button>
  </form>
  <div class="task">
    <li v-for="(task,index) in tasks" :key="task"> 
      <span>
        {{ task }}
        <button @click="deleteTask(index)">X</button>
      </span>
    </li>
  </div>
  <a v-bind:href="link">Udemy-Link</a>
</template>

<style scoped>
  h1{
    color: white;
  }
  .task {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .task li {
    color: springgreen;
  }
  button {
    height: 30px;
    font-size: 18px;
    border-radius: 10px;
    border: none;
    background-color: springgreen;
    color: #141414;
    transition: background-color 0.5s ease-in-out,color 0.5s ease-in-out;
  }
  button:hover {
    background-color: rgb(81, 7, 81);
    color: white;
  }
</style>

