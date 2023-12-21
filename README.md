
## Project structure

It's a monorepo with two packages, "@kniprepo/other" uses "@kniprepo/one" as a dependency:

```
packages
  |- one ................ (@kniprepo/one)
    |- src
      |- inner .......... (@kniprepo/one/inner)
        |- index.ts
          |-# foo(): void
  |-other ............... (@kniprepo/other)
    |- src
      |- index.ts ....... (entrypoint: import { test } from '@kniprepro/one/inner')

```


## Reproducing

1. `npm i` from the package root
2. `cd packages/one;   npm run build;  cd -`
3. `cd packages/other; npm run build;  cd -`
4. `cd packages/other; npm run start;  cd -` - ensure that everything works and "foo" is written to the stdout
5. `npm run knip`


### Output

```
Unused files (1)
packages/one/src/inner/index.ts
```


### Correct behavior

No unused files are reported