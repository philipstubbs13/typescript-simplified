# TypeScript Simplified

* <https://courses.webdevsimplified.com/view/courses/typescript-simplified>

```bash
npm i --save-dev typescript
```

```bash
npx tsc --init
```

```bash
npx tsc script.ts
```

```bash
npx tsc script.ts --noEmitOnError
```

```bash
npm create vite@latest .
```

* understanding the tsconfig
    * <https://github.com/tsconfig/bases>
    * <https://www.typescriptlang.org/tsconfig>

```bash
const SKILL_LEVELS = ["Beginner", "Intermediate", "Expert"] as const

type Person = {
    skillLevel: (typeof SKILL_LEVELS)[number]
}

SKILL_LEVELS.forEach(skillLevel => {
    console.log(skillLevel)
})
```

```bash
type APIResponse<TData = { status: number }> = {
    data: TData
    isError: boolean
}

type UserResponse = APIResponse<{ name: string, age: number}>

const a: UserResponse = {
    data: {
        name: "sdf",
        age: 324
    },
    isError: false
}
```

Pick and Omit
```bash
type Todo = {
    title?: string
    completed: boolean
    address?: {
        street?: string
    }
}
type RequiredPick<T, Key extends keyof T> = Required<Pick<T, Key>> & T
type PartialPick<T, Key extends keyof T> = Partial<Pick<T, Key>> & Omit<T, Key>

type FormTodo = RequiredPick<Todo, "title">

const todo: FormTodo = {
    completed: true
}
```

ReturnType and Parameters
```bash
function checkLength(a: string, b: number) {
    return a.length < b
}

type ReturnOfLengthCheck = ReturnType<typeof checkLength>
type Params = Parameters<typeof checkLength>
```

Record type
```bash
type PeopleGroupedByName = {
    [index: string]: Person[]
}

type PeopleGroupedByName = Record<Person["name"], Person[]>
```

Awaited type
```bash
async function doSomething() {
    return 3
}

type Value = Awaited<ReturnType<typeof doSomething>>
```

Unknown type
```bash
function func(data: unknown) {
    if (data != null && typeof data === 'object' && "name" in data && typeof data.name === "string") {
        console.log(data.name.length)
    }
}
```

Function Overloads
```bash
function sum(nums: number[]): number
function sum(a: number, b: number): number
function sum(a: number | number[], b?: number) {
    if (Array.isArray(a)) {
        return a.reduce()
    }

    if (b != null) {
        return a + b
    }
}

const s1 = sum([1, 2])
const s2 = sum(1, 2)

const s3 = sum([1, 2], 3)
```

Type Predicate Function
```bash
function print(obj: Person | Todo) {
    if (isPerson(obj)) {
        console.log(obj.name)
        return
    }

    console.log(obj.title)
}

function isPerson(obj: Person | Todo): obj is Person {
    return "name" in obj
}

const PRIORITIES = ["High", "Medium", "Low"] as const
type Priority = (typeof PRIORITIES)[number]
type Todo = {
    title: string
    description: string
}

function func(todo: Todo) {
    if (isPriority(todo.description)) {
        todo.description
    } else {
        todo.description
    }
}

function isPriority(description: string): description is Priority {
    return PRIORITIES.includes(description as Priority)
}
```