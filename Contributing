# Contributing

Contributions should preserve the core security model:

1. PTF tools remain persistent.
2. Engagement artifacts go under `_engagements/<client>/`.
3. Wipe routines must be scoped and conservative.
4. Do not add wrappers that silently write to persistent locations.
5. Do not claim secure deletion guarantees.

## Wrapper requirements

A wrapper should:

- check that an active workspace exists
- create its output directory
- use tool-native output flags where possible
- avoid writing to `/root`
- avoid hardcoded client names
- avoid deleting anything

## Documentation requirements

Document:

- command syntax
- output path
- known limitations

## Note to all contributors
If you try and can provide proof of work that is not AI generated (it will be checked) then you will be added to both 
this repo and the public repo at release. Any help is appreciated. 
