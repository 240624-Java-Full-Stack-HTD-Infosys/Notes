# Implementation

1. A function that displayes a welcome message.

welcome.ts

```ts
export function welcomeMessage(name: string){

    return "Welcome "+ name;

}
```

welcome.spec.ts

<i><b>Note:</b> every testing file has an extention spec.ts"</i>

```ts
import { welcomeMessage } from "./welcome";

describe('welcome', ()=>{
    it('should return welcome username',()=>{

        const result= welcomeMessage("Sheldon Cooper");
        expect(result).toContain("Sheldon Cooper");

    })
})
```

- `expect()` is used to the assert the result
- `toContain()` is used to check is a particular string is present in the returned string


karma debug:

![Welcome](/modules_new/resources/welcome.png)


2. A function compute that returns 0 if number is negative and increment of number if its positive.

compute.ts

```ts
export function compute(number: number){

    if(number <0){
        return 0;
    }
    else{
        return number +1;
    }

}
```

compute.spec.ts

```ts
import { compute } from "./compute";

describe('compute',() => {
    it('should return zero if number is negative',()=>{

        const result  = compute(-1);
        expect(result).toBe(0);

    })
    it('should return incremnt of number if number is positive',() =>{
        const result = compute(2);
        expect(result).toBe(3);

    })

})
```

- `toBe()` internally uses JavaScript `===`.
- It is used to match the actual and expected values.
- But `toBe()` fails where objects are not identical.
- To check deep equlity `toEqual()` is used.
- There is no difference between the two when comparing primitives. But for objects, `toEqual()` will compare by key/values-content, `toBe()` will compare by object reference.


karma debug:

![compute](/modules_new/resources/compute.png)
