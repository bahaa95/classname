
# @bahaa95/classname

A lightweight JavaScript function for conditional joining classNames together it also work with nested objects and array to improve readability and grouping.




[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)

[![Coverage Status](https://coveralls.io/repos/github/bahaa95/classname/badge.svg?branch=main)](https://coveralls.io/github/bahaa95/classname?branch=main)


## Installation

Install remove-unknown-properties

```bash
  #npm
  npm install @bahaa95/classname

  #yarn
  yarn add @bahaa95/classname
```
    
## Usage/Examples

```typescript
import { classname } from '@bahaa95/classname';

const isDisabled = false;
const isLoading = true;

const classnames = classname(
    "primary",
    null,
    " ",
    false && "border-blue",
    [true && "text-l"],
    {
      row:true,
      disabled: isDisabled || isLoading;
    }
);

console.log(classnames); //=> "primary text-l row disabled"

```
### Realtime Example
```typescript
import { classname as cx } from "@bahaa95/classname";

function App() {
  const [isActive, setIsActive] = useState(false);

  return (
    <div className="App">
      <input
        className={cx({
          cursur:true,
         //when a property has a value type of array or object the property name     
         //will not included in the result classes. it will use property name for 
         //grouping only in our case (text, active, display) properties below will not 
         //included to result.
          text: {
            "text-roboto": true,
            "text-l": true,
            "text-bold":false,
          },
          display:["flex","row","items-center"],
          active: isActive && ["border-blue", "bg-white", true && "text-black"],
        })}
        onFocus={() => setIsActive(true)}
        onBlur={() => setIsActive(false)}
      />
    </div>
  );
}
```