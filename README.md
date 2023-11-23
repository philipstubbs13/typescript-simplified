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