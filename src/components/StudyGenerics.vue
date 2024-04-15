<script setup lang="ts">
// 泛型 Generics
// 通用参数，用 generics. 比如当前类型可以接收 sting，也可以接收 number，这时候用 generics 来表示，会方便编写
// 思考：T 一会放前边，一会放后边
type GenericsArray<T> = T[]

interface MsgLine {
    id: number;
    name: string;
    age: number;
    class: string;
}

interface LogLine {
    date: number;
    handle: string;
}

interface Msg {
    infos: GenericsArray<MsgLine>;
    logs: GenericsArray<LogLine>;
}

interface PayloadMsg {
    code: number;
    msg: Msg;
}

const arrayNumber: GenericsArray<number> = [1, 2, 3]
const arrayString: GenericsArray<string> = ['1', '2', '3']

// fetch('xxxx').then((msg: Response) => {
    
// })
const msg: PayloadMsg = {
    code: 0,
    msg: { infos: [{ id: 1, name: 'fn', age: 18, class: '1班' }], logs: [{ date: new Date().getTime(), handle: 'test log' }] }
}
console.log(arrayNumber, arrayString, msg)

// 函数泛型

</script>
<template>

</template>
<style></style>