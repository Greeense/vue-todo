<template>
    <section>
        <ul>
            <li v-for="(todoItem,index) in propsdata" class="shadow">
                <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                {{ todoItem}}
                <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                    <i class="fas fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
    props : ['propsdata'],
    methods : {
        removeTodo(todoItem, index) {
            console.log(todoItem, index);
            localStorage.removeItem(todoItem); //로컬스토리지 데이터 삭제제
            this.todoItems.splice(index, 1); //배열의 특정 인덱스 삭제
        }
    }
})
</script>

<style>
    ul {
        list-style : none;
        padding-left : 0px;
        margin-top : 0;
        text-align : left;
    }
    li {
        display:flex;
        min-height:50px;
        height:50px;
        line-height:50px;
        margin:0.5rem 0;
        padding : 0 0.9rem;
        background:white;
        border-radius:5px;
    }

    .checkBtn {
        line-height:45px;
        color:#62acde;
        margin-right:5px;
    }

    .removeBtn {
        margin-left:auto;
        color:#de4343;
    }
</style>