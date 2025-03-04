# JavaScript 🟨

## Base

### Objective

- <details>
    <summary>
      <b>B1.</b> There are no unhandled errors while code executing.
    </summary>
    <p>

  While data loading and working with the app, there are no errors, the app does not break.

    </p>
  </details>

- **B2**. The code is cross-browser (the last versions of Chrome, Firefox and Safari), works correctly in LTS version of the server environment (NodeJS, Deno) and does not cause errors on different operating systems (Windows, Linux and MacOS).

### Markup

- <details>
    <summary>
      <b>B3.</b> There are no markup errors.
    </summary>
    <p>

  Validators:

  - https://validator.w3.org/nu/
  - https://caninclude.glitch.me/

  _Warnings are allowed._

    </p>
  </details>

- <details>
    <summary>
      <b>B4.</b> The minimum possible number of HTML elements has been used (no extra elements).
    </summary>
    <p>

  There should be no extra wrappers and blocks that are used for decoration and can be replaced with pseudo-elements.

    </p>
  </details>

- **B5**. Content images in `<img>` have the `alt` attribute filled.

- **B6**. The size is specified in the `<svg>` tag for inline SVG images.

- <details>
    <summary>
      <b>B7.</b> Vector graphics are used.
    </summary>
    <p>

  If there are svg images in the design, the use of PNG and other formats is prohibited.

    </p>
  </details>

### Styles

- **B8**. The layout of the blocks on the page is made by `flex` and/or `grid`.

- <details>
    <summary>
      <b>B9.</b> <code>!important</code> is forbidden.
    </summary>
    <p>

  The `important` keyword is only allowed for overrides in libraries. It is forbidden to use for writing your own styles.

    </p>
  </details>

- <details>
    <summary>
      <b>B10.</b> No global tag styles. Only class selectors or a cascade are used to set styles.
    </summary>
    <p>

  Global styles are only available in global style files (`scaffolding.css`, `app.css`, `reset.css` (🥲), etc).

  Bad:

  ```css
  /* components/items-list/styles.module.css */

  .wrapper div {
    display: flex;
  }

  p {
    text-align: center;
  }
  ```

  Good:

  ```css
  /* components/items-list/styles.module.css */

  .wrapper .column {
    display: flex;
  }

  .text {
    text-align: center;
  }
  ```

  Exceptions:

  `id` and other selectors other than `class` selector only allowed to be used to override libraries styles

  Bad

  ```css
  /* components/items-list/styles.module.css – YOUR component */

  #list-item {
    display: grid;
  }
  ```

  Good

  ```css
  /* components/accordion/styles.module.css – YOUR overrides to library components */

  #accordion {
    display: grid;
  }

  /* styles/scaffolding.css */

  /* root – default convention for the root element in React framework */
  #root {
    min-height: 100vh;
  }
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>B11.</b> Nesting of selectors is no more than two levels.
    </summary>
    <p>

  Bad

  ```css
  /* components/items-list/styles.module.css */

  .wrapper .column .text {
    text-align: center;
  }

  .wrapper {
    display: grid;

    .column {
      background-color: red;

      .text {
        text-align: center;
      }
    }
  }
  ```

  Good:

  ```css
  /* components/items-list/styles.module.css */

  .column .text {
    text-align: center;
  }

  .text {
    text-align: center;
  }

  .wrapper {
    display: grid;

    .column {
      background-color: red;
    }

    .text {
      text-align: center;
    }
  }
  ```

    </p>
  </details>

- **B12**. While interacting with elements (hovering, clicking, etc.), neither the element itself nor the elements around / inside its block change their position.

### Fonts

- **B13**. Non-standard fonts are connected locally.

- <details>
    <summary>
      <b>B14.</b> Alternate font options specified.
    </summary>
    <p>

  The font order:

  - Main font.
  - Safe font.
  - Font type.

  Example:

  ```css
  /* styles/scaffolding.css */

  body {
    font-family: Roboto, Arial, sans-serif;
  }
  ```

    </p>
  </details>

### Naming

- **B15.** Names of variables, parameters, properties and methods begin with a lowercase letter and are written in `camelCase` notation.

- <details>
    <summary>
      <b>B16.</b> English nouns are used as variable and property names.
    </summary>
    <p>

  Abbreviations in words are prohibited. Abbreviated variable names can be used only if the name is common (<code>err</code>, <code>xhr</code>, <code>evt</code>, <code>src</code>, <code>i</code> and etc).

    </p>
  </details>

- <details>
    <summary>
      <b>B17.</b> Variable names do not use the data type.
    </summary>
    <p>

  Bad:

  ```javascript
  const filtersArray = ['all', 'past', 'feature'];

  const catObject = {
    name: 'Pit',
    age: 7,
  };
  ```

  Good:

  ```javascript
  const filters = ['all', 'past', 'feature'];

  const cat = {
    name: 'Pit',
    age: 7,
  };
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>B18.</b> Arrays are named plural nouns.
    </summary>
    <p>

  Bad:

  ```javascript
  const age = [10, 15, 22];
  const name = ['John', 'Pit', 'Brew'];

  const cat = {
    name: 'Pit',
    friend: ['Nike', 'Sof', 'Kat'],
  };
  ```

  Good:

  ```javascript
  const ages = [10, 15, 22];
  const names = ['John', 'Pit', 'Brew'];

  const cat = {
    name: 'Pit',
    friends: ['Nike', 'Sof', 'Kat'],
  };
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>B19.</b> Boolean variables start with a prefix that can be answered with "yes".
    </summary>
    <p>

  Bad:

  ```javascript
  const login = true;

  const isNotRemoved = Boolean(!payload);
  if (isNotRemoved) {
  }

  const cat = {
    name: 'Pit',
    friend: false,
  };
  ```

  Good:

  ```javascript
  const isLogin = true;

  const isRemoved = Boolean(payload);
  if (!isRemoved) {
  }

  const cat = {
    name: 'Pit',
    hasFriends: false,
  };
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>B20.</b> Function or method begins with a verb.
    </summary>
    <p>

  Exceptions:

  Handler functions or callbacks.

  Bad:

  ```javascript
  const action = (names) => {
    console.log(names);
  };

  const cat = {
    name: 'Pit',
    action() {
      console.log('Meow');
    },
  };

  const randomNumber = () => Math.random();
  ```

  Good:

  ```javascript
  const printNames = (names) => {
    console.log(names);
  };

  const cat = {
    name: 'Pit',
    say() {
      console.log('Meow');
    },
  };

  const getRandomNumber = () => Math.random();
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>B21.</b> Classes are named with English nouns. The class name starts with a capital letter.
    </summary>
    <p>

  Bad:

  ```typescript
  class wizard {}
  ```

  Good:

  ```typescript
  // class
  class Wizard {}
  ```

    </p>

  In cases when there is one or more acronyms in the class name, it should have the first acronym in uppercase whereas all others be handled as a regular word (only the first letter is capitalized)

  Bad:

  ```typescript
  class XmlHttpRequest {}
  ```

  Good:

  ```typescript
  class XMLHttpRequest {}
  ```

  </details>

- <details>
    <summary>
      <b>B22.</b> Constant names are written in capital letters.
    </summary>
    <p>

  Words are separated by underscores (`UPPER_SNAKE_CASE`), for example:

  ```javascript
  const MAX_HEIGHT = 6996;
  const IDX_NOT_FOUND = -1;
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>B23.</b> Enums are named by English nouns and begin with an uppercase (capital) letter. Keys are declared in constant format (with uppercase letters).
    </summary>
    <p>

  Bad:

  ```typescript
  const statusCodes = {
    ok: 200,
    notFound: 404,
    badRequest: 400,
  };
  ```

  Good:

  ```typescript
  const StatusCode = {
    OK: 200,
    NOT_FOUND: 404,
    BAD_REQUEST: 400,
  };
  ```

    </p>

  In cases when there is one or more acronyms in the enum name, it should have the first acronym in uppercase whereas all others be handled as a regular word (only the first letter is capitalized)

  Bad:

  ```typescript
  const HttpStatusCode = {};
  ```

  Good:

  ```typescript
  const HTTPStatusCode = {};
  ```

  </details>

- <details>
    <summary>
      <b>B24.</b> <code>kebab-case</code> is used to name files/folders (names are written in lowercase letters, words are separated by hyphens).
    </summary>
    <p>

  In order to avoid name conflicts in different operating systems, it is better to use the least conflicting way of naming files — lowercase letters separated by a hyphen.

  Bad

  ```typescript
  // src/components/common/Button/Button.tsx
  // src/services/UserService/UserService.ts
  ```

  Good

  ```typescript
  // src/components/common/button/button.tsx
  // src/services/user-service/user-service.ts
  ```

  Exceptions:

  Framework/library files that cannot work with another case.

    </p>
  </details>

- **B25.** There is no transliteration in any form (in file names, classes, variables, etc.).

### Formatting

- <details>
    <summary>
      <b>B26.</b> The code matches the style of the project.
    </summary>
    <p>

  There are no errors while checking the project with linters (ESLint, StyleLint, Prettier, etc). All types of linters are at the discretion of the team.

  Rules are not disabled anywhere in the source code.

    </p>
  </details>

- <details>
    <summary>
      <b>B27.</b> Curly braces are required everywhere.
    </summary>
    <p>

  In any constructions that imply the use of a code block (curly braces), such as `for`, `while`, `if`, `switch`, `function`, the code block is necessarily used, even if the statement consists of one line.

  Bad

  ```typescript
  if (x % 2 === 1) isEven = false;

  switch (actionType) {
    case ActionType.START_LOADING:
      return {
        ...state,
        isLoading: true,
      };
    case ActionType.END_LOADING:
      return {
        ...state,
        isLoading: false,
      };
  }
  ```

  Good

  ```typescript
  if (x % 2 === 1) {
    isEven = false;
  }

  switch (actionType) {
    case ActionType.START_LOADING: {
      return {
        ...state,
        isLoading: true,
      };
    }
    case ActionType.END_LOADING: {
      return {
        ...state,
        isLoading: false,
      };
    }
  }
  ```

  The exceptions are single-line arrow functions, which can be used without the required blocks of code:

  ```typescript
  const checkedCheckboxes = checkboxes.filter((checkbox) => checkbox.checked);
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>B28.</b> All source files follow the recommended structure.
    </summary>
    <p>

  ```typescript
  // 1. Imports
  import { getUniqueItems } from 'helpers';

  // 2. Types / Variables whose value is known before the program starts
  const COLORS = ['red', 'green', 'blue'];

  // 3. Variables whose value is known before main code execution
  const colorPicker = document.querySelector('.color-picker');

  // 4. Functions
  const getUniqueColors = (userColors, defaultColors) => {
    return getUniqueItems(userColors, defaultColors);
  };

  // 5. Program code
  const rightColors = getColorsIntersection(colorPicker.value, DEFAULT_COLORS);

  // 6. Exports
  export { rightColors };
  ```

  Some blocks may be missing, but the rest should still adhere to the order.

    </p>
  </details>

- <details>
    <summary>
      <b>B29.</b> Sets of constants of the same type are collected into Enums.
    </summary>
    <p>

  Bad:

  ```typescript
  const LOAD_USERS_START = 'LOAD_USERS_START';
  const LOAD_USERS_END = 'LOAD_USERS_END';
  const LOAD_USERS_ERROR = 'LOAD_USERS_ERROR';
  ```

  Good:

  ```typescript
  const UserAction = {
    LOAD_START: 'LOAD_START',
    LOAD_END: 'LOAD_END',
    LOAD_ERROR: 'LOAD_ERROR',
  };
  ```

    </p>
    <p>
    Note: constants that are used in the same context, but has different purposes should be split into different enums or separate constants

  Bad:

  ```typescript
  const CompensationComputation = {
    HOLIDAY_COMPENSATION: 1.7,
    OVERTIME_COMPENSATION: 1.5,
    OVERTIME_THRESHOLD: 1.1, //related not to compensation rate, but to overtime hours calculation
  };
  ```

  Good:

  ```typescript
  const CompensationCoefficient = {
    HOLIDAY_COMPENSATION: 1.7,
    OVERTIME_COMPENSATION: 1.5,
  };

  const OVERTIME_THRESHOLD = 1.1;
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>B30.</b> All class properties and methods are marked with member access (private , public or protected).
    </summary>
    <p>

  Bad:

  ```typescript
  class Animal {
    constructor({ name }) {
      this.privateName = name;
    }

    getPrivateName() {
      return this.privateName;
    }
  }
  ```

  Good:

  ```typescript
  class Animal {
    #privateName;

    public constructor({ name }) {
      this.#privateName = name;
    }

    public getPrivateName() {
      return this.#privateName;
    }
  }

  // or

  class Animal {
    private privateName;

    public constructor({ name }) {
      this.privateName = name;
    }

    public getPrivateName() {
      return this.privateName;
    }
  }
  ```

    </p>
  </details>

- **B31**. The code does not use “magic values”, each of them has a separate variable named as a constant.

### Rubbish

- <details>
    <summary>
      <b>B32.</b> The versions of dependencies used are fixed in <code>package.json</code>.
    </summary>
    <p>

  The dependency lists in the package.json file indicate the exact versions of the packages used. The version must be specified. `^`, `*` and `~` are not allowed.

    </p>
  </details>

- <details>
    <summary>
      <b>B33.</b> There are no unused dependencies in the project.
    </summary>
    <p>

  Node: Some dependencies are needed by other dependencies. Ex. `pg` package is required for most of ORM packages.

    </p>
  </details>

- <details>
    <summary>
      <b>B34.</b> There are no files, modules and parts of code that are not used in the project code, including commented code pats.
    </summary>
    <p>

  There are no script files that are “dead code” that is never executed.

    </p>
  </details>

### Correctness

- **B35.** Constants and enums are not redefined anywhere in the code.

- <details>
    <summary>
      <b>B36.</b> Potentially incorrect operations are missing. API is used correctly.
    </summary>
    <p>

  For example, sum of two values with different data types.

  Bad:

  ```typescript
  new Date() + 1000;
  ```

  Good:

  ```typescript
  Number(new Date()) + 1000;
  ```

  Potentially incorrect operation of taking the integer part of a number.

  Bad:

  ```typescript
  const minutesNumber = ~~(seconds / 60);
  ```

  Good:

  ```typescript
  const minutesNumber = Math.trunc(seconds / 60);
  ```

  Valid values are passed as expected by the specification.

  Bad:

  ```typescript
  const isPressed = element.getAttribute('aria-pressed', false);
  ```

  Good:

  ```typescript
  const isPressed = element.getAttribute('aria-pressed');
  ```

  `map` method returns a value, so either this value should be used, or the method should be replaced with `forEach`.

  Bad:

  ```typescript
  let greeting = 'Hey';

  wizards.map((wizard) => {
    greeting += `, ${wizard.name}`;
  });

  console.log(`${greeting}!`);
  ```

  Good:

  ```typescript
  const greeting = 'Hey';

  const names = wizards.map((wizard) => {
    return wizard.name;
  });

  console.log(`${greeting} ${names.join(', ')}!`);
  ```

    </p>
  </details>

### Modules

- <details>
    <summary>
      <b>B37.</b> Modules do not export mutable variables.
    </summary>
    <p>
    A module should not export a variable whose value may change in the future.

  Bad:

  ```typescript
  let latestResult;

  export { latestResult };
  ```

  Good:

  ```typescript
  const latestResult = loadLatestResult();

  export { latestResult };
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>B38.</b> The name of the module corresponds to its content.
    </summary>
    <p>

  Different logical parts of the code are placed in separate module files. The name of the module must match its content. For example, if the module contains the `GameView` class, then the name of the module should be `game-view.js`.

    </p>
  </details>

- **B39.** No `index` files. `index` file can be only used as the entry point of the application.

### Security

- <details>
    <summary>
      <b>B40.</b> Event handlers are added and removed in a timely manner.
    </summary>
    <p>

  Event handlers are added only when the element appears on the page and are removed when it disappear.

    </p>
  </details>

### Database

- **B41**. 🗄 It is forbidden to use the GET method to write data.

- <details>
    <summary>
      <b>B42.</b> 🗄 There are no SQL Injections in the code.
    </summary>
    <p>

  While working with a database, all SQL queries must be protected from SQL injection.

    </p>
  </details>

- <details>
    <summary>
      <b>B43.</b> 🗄 Code protected from XSS.
    </summary>
    <p>

  It is not allowed to display unfiltered information received from the user, because XSS attack is possible.

    </p>
  </details>

- **B44.** 🗄 Passwords are always hashed.

- **B45.** 🗄 Migrations roll in two ways (up and down) without any errors. Data consistency is preserved after every migration.

## Advance

### Objective

- <details>
    <summary>
      <b>A1.</b> Modern syntax is preferred.
    </summary>
    <p>

  Prefer modern JS syntax if possible, based on your target of your bundler, usage of transpilers (ex. Babel) and the browsers/platforms you support. See some examples below

  **Array methods:**

  Bad:

  ```typescript
  items.slice().reverse();
  ```

  Good:

  ```typescript
  items.toReversed();
  ```

  **Optional Chaining:**

  Bad:

  ```typescript
  const userName = user && user.name;
  ```

  Good:

  ```typescript
  const userName = user?.name;
  ```

  **Nullish coalescing:**

  Bad:

  ```typescript
  const userCreatePayload = payload || INITIAL_USER_CREATE_PAYLOAD_VALUES;
  ```

  Good:

  ```typescript
  const userCreatePayload = payload ?? INITIAL_USER_CREATE_PAYLOAD_VALUES;
  ```

  **Top-level await:**

  Bad:

  ```typescript
  (async () => {
    await app.run();
  })();
  ```

  Good:

  ```typescript
  await app.run();
  ```

    </p>
  </details>

### Markup

- <details>
    <summary>
      <b>A2.</b> All interactive elements have a description.
    </summary>
    <p>

  Bad:

  ```tsx
  <input placeholder="First Name" />

  <button onClick={handleEditUserClick}></button>

  <a href={AppRoute.DASHBOARD}></a>

  <button onClick={handleEditUserClick}><img src="img/user.svg" /></button>

  <a href={AppRoute.DASHBOARD}><img src="img/arrow.svg" /></a>
  ```

  Good:

  ```tsx
  <label class="visually-hidden" for="first-name">First name</label>
  <input id="first-name" placeholder="First Name" />

  <button onClick={handleEditUserClick}>
    <span className="visually-hidden">Edit user</span>
  </button>

  <a href={AppRoute.DASHBOARD}>
    <span className="visually-hidden">Go to dashboard</span>
  </a>

  <label>
    <span class="visually-hidden">First name</span>
    <input placeholder="First Name" />
  </label>

  <button onClick={handleEditUserClick}>
    <img src="img/user.svg" alt="" />
    <span className="visually-hidden">Edit user</span>
  </button>

  <a href={AppRoute.DASHBOARD}>
    <img src="img/arrow.svg" alt="" />
    <span className="visually-hidden">Go to dashboard</span>
  </a>

  <input aria-label="First name" placeholder="First Name" />
  ```

    </p>
  </details>

### Naming

- <details>
    <summary>
      <b>A3.</b> Uniform writing and formatting of code in all file types (HTML, CSS, JS, JSX, ect.).
    </summary>
    <p>

  Example:

  If you use css-nesting it should be used through all the project (all style files must be written using nesting). If you use interfaces with `I` (ex. `IUser`) approach it should be used through all the project (all interfaces must be written with `I` prefix). If you use TS Enums approach it should be used through all the project (you can not use both TS Enum and JS Enum (JS plain object with `as const`)).

    </p>
  </details>

- **A4.** Abstract classes or interfaces should have generic names and do not contain implementation details.

- <details>
    <summary>
      <b>A5.</b> The names of methods/functions and properties/variables of objects do not contain the names of object/module.
    </summary>
    <p>

  Bad:

  ```typescript
  const popup = {
    openPopup() {
      console.log('I will open popup');
    },
  };

  const wizard = {
    wizardName: 'Gandalf',
  };
  ```

  Good:

  ```typescript
  const popup = {
    open() {
      console.log('I will open popup');
    },
  };

  const wizard = {
    name: 'Gandalf',
  };
  ```

  Bad:

  ```typescript
  // src/validation-schemas/users/login.validation-schema.ts

  const userValidationSchema = {};
  ```

  Good:

  ```typescript
  // src/validation-schemas/users/login.validation-schema.ts

  const user = {};

  // src/components/sign-in/sign-in.tsx
  import { user as userValidationSchema } from 'validation-schemas';
  ```

    </p>
  </details>

### Uniformity

- **A6**. 🔵 Interfaces are only used to `implement` a class.

- <details>
    <summary>
      <b>A7.</b> A uniform naming style for variables is used.
    </summary>
    <p>

  Variable naming style is used the same in all modules, for example:

  If the variables that store the DOM element contain the word Element or anything else, it must be the same everywhere

  Bad:

  ```typescript
  const popupMainElement = document.querySelector('.popup');
  const sidebarNode = document.querySelector('.sidebar');
  const similarContainer = popupMainElement.querySelector('ul.similar');
  ```

  Good:

  ```typescript
  const popupMainElement = document.querySelector('.popup');
  const sidebarElement = document.querySelector('.sidebar');
  const similarContainerElement = popupMainElement.querySelector('ul.similar');
  ```

  Also good

  ```typescript
  const popupMainNode = document.querySelector('.popup');
  const sidebarNode = document.querySelector('.sidebar');
  const similarContainerNode = popupMainNode.querySelector('ul.similar');
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>A8.</b> One approach is used while using API that supports multiple approaches.
    </summary>
    <p>

  If there are several different APIs that allow you to solve the same problem, for example, finding an element by id in the DOM tree, then only one of these APIs is used in the project.

  Bad:

  ```typescript
  const popupMainElement = document.querySelector('#popup');
  const sidebarElement = document.getElementById('sidebar');

  const popupClassName = popupMainElement.getAttribute('class');
  const sidebarClassName = sidebarElement.className;
  ```

  Good:

  ```typescript
  const popupMainElement = document.querySelector('#popup');
  const sidebarElement = document.querySelector('#sidebar');

  const popupClassName = popupMainElement.getAttribute('class');
  const sidebarClassName = sidebarElement.getAttribute('class');

  // or

  const popupMainElement = document.getElementById('popup');
  const sidebarElement = document.getElementById('sidebar');

  const popupClassName = popupMainElement.className;
  const sidebarClassName = sidebarElement.className;
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>A9.</b> ⚛️ Callbacks passed to <code>props</code> are named with <code>on</code> prefix.
    </summary>
    <p>
  ```tsx
  <ListItem onClick={handleBtnClick} />
  ```
    </p>
  </details>

- <details>
    <summary>
      <b>A10.</b> ⚛️ Component functions are named with <code>handle</code> prefix.
    </summary>
    <p>

  ```jsx
  const Dashboard = () => {
    const handleBtnClick = () => {};

    return <ListItem onClick={handleBtnClick} />;
  };
  ```

    </p>
  </details>

### Modules

- **A11.** If the same code is repeated in several modules, the repeated part is moved to a separate module.

### Redundancy

- <details>
    <summary>
      <b>A12.</b> Where possible, the ternary operator is used in the assignment of a value instead of if.
    </summary>
    <p>

  Exceptions:

  Ternary operator should not be nested.

  Bad:

  ```typescript
  let sex;

  if (isMale) {
    sex = 'Man';
  } else {
    sex = 'Woman';
  }
  ```

  Good:

  ```typescript
  const sex = isMale ? 'Man' : 'Woman';
  ```

    </p>
  </details>

- <details>
    <summary>
      <b>A13.</b> Conditions are simplified.
    </summary>
    <p>

  If the function returns a boolean value, do not use `if..else` with unnecessary `return`.

  Bad:

  ```typescript
  const checkIsEquals = (firstValue, secondValue) => {
    if (firstValue === secondValue) {
      return true;
    } else {
      return false;
    }
  };
  ```

  Good:

  ```typescript
  const checkIsEquals = (firstValue, secondValue) => {
    return firstValue === secondValue;
  };
  ```

    </p>
  </details>

### Optimality

- **A14**. 🔵 `unknown` is preferred over `any`. `any` is prohibited.

- <details>
    <summary>
      <b>A15.</b> Use the <code>for/of</code> to iterate over arrays and data structures that can be iterated over(Iterable).
    </summary>
    <p>

  Where an array element index is not required, or where all elements of an iterable data structure need to be traversed, a `for .. of` loop is used instead of a `for` loop.

  Bad:

  ```typescript
  for (let i = 0; i < levels.length; i++) {
    const level = levels[i];
    renderLevel(level);
  }
  ```

  Good:

  ```typescript
  for (const level of levels) {
    renderLevel(level);
  }
  ```

    </p>
  </details>

### Complexity and Readability

- **A16.** Long functions and methods are split into several smaller ones.

- <details>
    <summary>
      <b>A17.</b> Iterators for arrays are used to work with JS collections.
    </summary>
    <p>

  Iterators are used to with arrays — `forEach`, `map`, `filter`, and etc.

  ```typescript
  elements.forEach((element) => {
    element.addEventListener('click', () => {
      console.log(element);
    });
  });
  ```

    </p>
  </details>
