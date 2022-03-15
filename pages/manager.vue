<template>
<div class="flex items-center justify-center min-h-screen bg-gray-100">
    <div class="p-8 bg-white shadow-lg">
        <div class="flex items-center mb-8">
            <label for="" class="mr-4"> Tarea: </label>
            <input 
                class="form-control border border-solid rounded px-2 py-1 mr-4 border-gray-300" 
                id="task-input" type="text" v-model="taskInput" @keyup.enter="addTask" v-on:keypress="isLetter($event)"
            >
            <button @click="addTask" class="inline-block px-6 py-2.5 bg-blue-600 text-white font-medium text-xs rounded shadow-md hover:bg-blue-700 transition duration-150 ease-in-out">
                Agregar
            </button>
        </div>

        <ul class="list-none hover:list-disc">
            <li 
                v-for="task in tasks"
                :key="task.id"
                class="flex items-center space-between"
            >
                <input type="checkbox" v-model="task.completed" class="form-check-input h-4 w-4 border border-gray-300 rounded-sm bg-white checked:bg-blue-600 checked:border-blue-600 focus:outline-none transition duration-200 bg-no-repeat bg-center bg-contain float-left cursor-pointer">

                <label class="form-check-label inline-block text-gray-800 flex-1 ml-4 my-2.5" for="">{{ task.title }}</label>            

                <button v-show="!task.completed" @click="removeTask(task)" class="inline-block border-2 px-4 py-2.5 text-gray-700 font-medium text-xs leading-tight uppercase rounded hover:bg-gray-300 hover:shadow-lg focus:bg-gray-300 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-gray-400 active:shadow-lg transition duration-150 ease-in-out">
                    x
                </button>
            </li>
        </ul>
    </div>
</div>
</template>

<script>
export default {
    
    name: 'ManagerPage',
    data() {
        return {
            tasks: [],
            taskInput: ""
        }
    },
    methods: {
        addTask(){
        
            if (this.taskInput !== ""){
                this.tasks.push({
                    id: Date.now(),
                    title: this.taskInput,
                    completed: false
                });

                this.taskInput = "";
            }
        },
        removeTask(task){
            this.tasks.splice(this.tasks.indexOf(task), 1)
        },
        isLetter(e) {
            let char = String.fromCharCode(e.keyCode);
            if(/^[A-Za-z0-9]+$/.test(char)) return true;
            else e.preventDefault();
        }
    }
}
</script>
