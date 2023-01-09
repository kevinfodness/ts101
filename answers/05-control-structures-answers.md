# Quiz 5: Control Structures

## 1. Given the following program:

```ts
let count: number
if (count > 10) {
    console.log("You have made too many selections.")
} else if (count < 10) {
    console.log("Please select 10 items from the list.")
} else {
    console.log("If these selections are correct, please proceed to the next step.")
}
```

### a. What is the output of the program if `count = 11`?

- [X] `You have made too many selections.`
- [ ] `Please select 10 items from the list.`
- [ ] `If these selections are correct, please proceed to the next step.`

### b. What is the output of the program if `count = 9`?

- [ ] `You have made too many selections.`
- [X] `Please select 10 items from the list.`
- [ ] `If these selections are correct, please proceed to the next step.`

### c. What is the output of the program if `count = 10`?

- [ ] `You have made too many selections.`
- [ ] `Please select 10 items from the list.`
- [X] `If these selections are correct, please proceed to the next step.`

## 2. Given the following program:

```ts
let chemical: string
switch (chemical) {
    case "chemical-x":
        console.log("Store at room temperature.")
        break
    case "chemical-y":
        console.log("Store in the refrigerator.")
        break
    case "chemical-z":
        console.log("Store in the freezer.")
        break
    default:
        console.log("Unknown chemical specified.")
        break
}
```

### a. What is the output of the program if `chemical = "chemical-y"`?

- [ ] `Store at room temperature.`
- [X] `Store in the refrigerator.`
- [ ] `Store in the freezer.`
- [ ] `Unknown chemical specified.`

### b. What is the output of the program if `chemical = "chemical-z"`?

- [ ] `Store at room temperature.`
- [ ] `Store in the refrigerator.`
- [X] `Store in the freezer.`
- [ ] `Unknown chemical specified.`

### c. What is the output of the program if `chemical = "chemical-q"`?

- [ ] `Store at room temperature.`
- [ ] `Store in the refrigerator.`
- [ ] `Store in the freezer.`
- [X] `Unknown chemical specified.`

### d. What is the output of the program if `chemical = "chemical-x"`?

- [X] `Store at room temperature.`
- [ ] `Store in the refrigerator.`
- [ ] `Store in the freezer.`
- [ ] `Unknown chemical specified.`

## BONUS: Given the following program, what is the output if `value = 4`?

```ts
let value: number
let tax: number = 0
switch (value) {
    case 1:
        tax = 0.05
        break
    case 2:
        tax = 0.10
    case 3:
        tax = 0.15
        break
    case 4:
        tax = 0.20
    case 5:
        tax = 0.25
        break
    default:
        tax = 0
        break
}
console.log(tax)
```

- [ ] `0`
- [ ] `0.05`
- [ ] `0.10`
- [ ] `0.15`
- [ ] `0.20`
- [X] `0.25`
