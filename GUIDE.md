# Developer guide while building with Circles

## Getting set up

- install Foundry, create new repo with `forge init <repo>`
- install Circles contracts dependency with
   ```
   forge install aboutcircles/circles-contracts-v
   cd lib/circles-contracts-v2
   git fetch
   git checkout 20240614-integration-groups
   cd ../..
   git add -A & git commit
   ```