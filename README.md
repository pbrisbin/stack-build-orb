# Stack Build Orb [![CircleCI status](https://circleci.com/gh/pbrisbin/stack-build-orb.svg "CircleCI status")](https://circleci.com/gh/pbrisbin/stack-build-orb)

Built, test, and lint Stack-based Haskell projects in your CircleCI jobs.

## Usage

```yaml
version: 2.1

orbs:
  stack-build: pbrisbin/stack-build@x.y

jobs:
  stack-build:
    executor: stack-build/ubuntu
    steps:
      - checkout
      - stack-build/setup
      - stack-build/build

workflows:
  commit:
    jobs:
      - stack-build:
          name: "default"
      - stack-build:
          name: "ghc-8.8.3 / lts-15.12"
          stack-yaml: stack-lts-15.12.yaml
      - stack-build:
          name: "ghc-8.6.5 / lts-14.27"
          stack-yaml: stack-lts-14.27.yaml
      - stack-build:
          name: "ghc-8.4.3 / lts-12.10"
          stack-yaml: stack-lts-12.10.yaml
      - stack-build:
          name: "nightly"
          stack-yaml: stack-nightly.yaml
          stack-arguments: --resolver nightly
          hlint: false
          weeder: false
```

---

[LICENSE](./LICENSE) | [CHANGELOG](./CHANGELOG.md)
