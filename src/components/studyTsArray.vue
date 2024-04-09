<script lang="ts">
interface Person_In {
    name: string;
}

type Person_Tp = {
    name: string;
}

type Salary_Tp = {
    salary: number;
    type: string;
}
const arr: Person_Tp[] = [{ name: 'zs' }, { name: 's' }]
console.log(arr)

// Partial 令传入的类型所有属性变成可选
type Em = Partial<Person_Tp> & Partial<Salary_Tp>

const arrSalary: Em[] = [
    { name: 'zs', salary: 9999, type: 'USD' },
    { name: 'zs', salary: 9999 },
    { name: 'zs' },
    {}
]

interface Eminterface extends Person_Tp {
    salary: number;
    type: string;
}

interface Eminterface extends Person_In {
    salary: number;
    type: string;
}

const arrEm: Partial<Eminterface>[] = [
    { name: 'zs', salary: 9999, type: 'USD' },
    { name: 'zs', salary: 9999 },
    { name: 'zs' },
    {}
]

console.log(arrEm)
console.log(arrSalary)


type A = {
    name: string;
};

interface B extends A {
    age: number;
};

const b: B = { name: "Alice", age: 30 }; // 

console.log(b)

// 元组 - 装的是 只有2个元素，第一个元素是 number 类型，第二个元素是 string 类型的数组
const arrs: [number, string] = [1, 'ss']

console.log(arrs)

// ** interface 定义类型，强调结构，注意没有 “=” 号
interface PersonInterface {
    name: string;
    age: number;
}

// ** type 定义 类型 别名，注意 type 定义中有 “=” 号，type Xx = ...，type 定义更灵活，强调别名，可以给interface 定义的类型 改个名字，如：type Xx = XxInterfaceType
type PersonType = {
    name: string;
    age: number;
}

const arr1: PersonType[] = [{ name: 'zs', age: 18 }]
const arr2: PersonInterface[] = [{ name: 'zs', age: 18 }]
const arr3: (PersonInterface & { age: number }) [] = [{ name: 'zs', age: 18 }]
// Partial 可选
const arr4: Partial<PersonInterface>[] = [{ name: 'xx' }, {}]
console.log(arr1, arr2, arr3, arr4)

</script>
<template>

</template>
<style></style>
