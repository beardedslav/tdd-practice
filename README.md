# tdd-practice

## Setup

- One time setup: `npm install`
- Run test: `npm test`

## Instructions

- write a function canAdmitToNightClub that takes a person object as an argument and returns true if they can be admitted and false if they cannot
- an unaccompanied minor (under the age of 18) may not be admitted
- any person who is visibly inebriated may not be admitted
- the person object should have the following fields
  - age (Number)
  - isAccompaniedByAdult (Boolean)
  - isVisiblyInebriated (Boolean)

### Step 1

Step 1 is "Red" (write a failing test). For each of the following determine if the tests are now passing or failing and explain whether this is an ok proposal for this step and why (not)?

a) <details><summary>Answer:</summary> Failing. This is ok. It is a good first failing test (maybe making the person exactly 18 would be better)</details>
Code being tested

```javascript
function canAdmitToNightClub() {}
```

Tests

```javascript
test("returns true for a person over 18", () => {
  const personOver18 = {
    age: 30,
    isVisiblyInebriated: false,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(personOver18)).toBe(true);
});
```

b) <details><summary>Answer:</summary> Failing. This is ok. It is a good first failing test (it could be argued that the person argument and return false are not strictly needed in the code to be tested)</details>
Code being tested

```javascript
function canAdmitToNightClub(person) {
  return false;
}
```

Tests

```javascript
test("returns true for a person over 18", () => {
  const personOver18 = {
    age: 30,
    isVisiblyInebriated: false,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(personOver18)).toBe(true);
});
```

c) <details><summary>Answer:</summary> Passing. This is not ok. The test passes instead of failing</details>
Code being tested

```javascript
function canAdmitToNightClub(person) {
  return true;
}
```

Tests

```javascript
test("returns true for a person over 18", () => {
  const personOver18 = {
    age: 30,
    isVisiblyInebriated: false,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(personOver18)).toBe(true);
});
```

d) <details><summary>Answer:</summary> Failing. This is not ok. There are 2 failing tests (when you have more experience you might find that writing 2 tests instead of one is occasionally the best thing to do</details>
Code being tested

```javascript
function canAdmitToNightClub() {}
```

Tests

```javascript
test("returns true for a person over 18", () => {
  const personOver18 = {
    age: 30,
    isVisiblyInebriated: false,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(personOver18)).toBe(true);
});

test("returns false for a person under 18", () => {
  const personUnder18 = {
    age: 17,
    isVisiblyInebriated: false,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(personUnder18)).toBe(false);
});
```

### Step 2

Step 1 is "Green" (make the test pass). Assuming we start with answer a) from step 1, for each of the following determine if the tests are now passing or failing and explain whether this is an ok proposal for this step and why (not)?

a) <details><summary>Answer:</summary> Failing. This is not ok. The test fails instead of passing</details>
Code being tested

```javascript
function canAdmitToNightClub(person) {
  return false;
}
```

Tests

```javascript
test("returns true for a person over 18", () => {
  const personOver18 = {
    age: 30,
    isVisiblyInebriated: false,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(personOver18)).toBe(true);
});
```

b) <details><summary>Answer:</summary> Passing. This is ok. The test now passes</details>
Code being tested

```javascript
function canAdmitToNightClub(person) {
  return true;
}
```

Tests

```javascript
test("returns true for a person over 18", () => {
  const personOver18 = {
    age: 30,
    isVisiblyInebriated: false,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(personOver18)).toBe(true);
});
```

c) <details><summary>Answer:</summary> Passing. This is not ok. The test passes, but we have written too much code. This might not seem like a bad thing, but it is now not possible to write a failing test for a person under 18</details>
Code being tested

```javascript
function canAdmitToNightClub(person) {
  return person.age > 18;
}
```

Tests

```javascript
test("returns true for a person over 18", () => {
  const personOver18 = {
    age: 30,
    isVisiblyInebriated: false,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(personOver18)).toBe(true);
});
```

Step 3

Step 3 is Refactor. There is not much to refactor yet, so let's move on to Step 4.

Step 4

Step 4 is Red. Assuming we start with answer b) from step 2, for each of the following determine if the tests are now passing or failing and explain whether this is an ok proposal for this step and why (not)?

a) <details><summary>Answer:</summary> Failing. This is ok. This a good next failing test</details>
Code being tested

```javascript
function canAdmitToNightClub(person) {
  return true;
}
```

Tests

```javascript
test("returns true for a person over 18", () => {
  const personOver18 = {
    age: 30,
    isVisiblyInebriated: false,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(personOver18)).toBe(true);
});

test("returns false for a person under 18", () => {
  const personUnder18 = {
    age: 17,
    isVisiblyInebriated: false,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(personUnder18)).toBe(false);
});
```

b) <details><summary>Answer:</summary> Failing. This is ok. But it's probably not the best next failing test as we have started our tests by working with a person's age (according to the written description)</details>
Code being tested

```javascript
function canAdmitToNightClub(person) {
  return true;
}
```

Tests

```javascript
test("returns true for a person over 18", () => {
  const personOver18 = {
    age: 30,
    isVisiblyInebriated: false,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(personOver18)).toBe(true);
});

test("returns false for an inebriated person", () => {
  const inebriatedPerson = {
    age: 18,
    isVisiblyInebriated: true,
    isAccompaniedByAdult: false,
  };
  expect(canAdmitToNightClub(inebriatedPerson)).toBe(false);
});
```
