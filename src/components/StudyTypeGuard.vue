<script setup lang="ts">
interface Teacher {
    name: string;
    subject: string;
}

interface Person {
    name: string;
}

function showTypeGuardAndTypePredicates (someone: Person | Teacher) {
    // // 这里访问 someone 的 subject 属性会编译报错，因为 subject 属性不同时存在两个类型中。那我们想要用 subject 怎么办呢？就需要类型守卫
    // // This place to visite someone's subject attribute will be Throw error, cause subject attribute is not in each types. So how can we do if we want subject attribute? We need Type Guard. 
    // console.log(someone.subject)

    // Teacher Type Guard
    function isTeacherTypeGurad (p: Person | Teacher): p is Teacher {
        return (p as Teacher).subject !== undefined
    }

    // Use Type Guard to visite someone.subject
    if (isTeacherTypeGurad(someone)) {
        console.log(someone.subject)
    }
}

const teacher: Teacher = {
    name: 'xx',
    subject: 'TS'
}

showTypeGuardAndTypePredicates(teacher)
</script>
<template>
    <h1>类型守卫 Type Guard</h1>
    <!-- <div></div> -->
</template>
<style></style>