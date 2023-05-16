**Archived**: development on this project will continue in [this fork][fork]. Existing
versions of the Orb will not be removed, but updates will be published under the [fork's
orb][orb].

[fork]: https://github.com/stackbuilders/stack-build-orb
[orb]: https://circleci.com/developer/orbs/orb/stackbuilders/stack-build

# Stack Build Orb [![CircleCI status](https://circleci.com/gh/pbrisbin/stack-build-orb.svg "CircleCI status")](https://circleci.com/gh/pbrisbin/stack-build-orb)

Built, test, and lint Stack-based Haskell projects in your CircleCI jobs.

## Usage

```yaml
version: 2.1

orbs:
  stack-build: pbrisbin/stack-build@x.y

workflows:
  commit:
    jobs:
      - stack-build/build-test-lint:
          name: "default"
      - stack-build/build-test-lint:
          name: "ghc-8.8.3 / lts-15.12"
          stack-yaml: stack-lts-15.12.yaml
      - stack-build/build-test-lint:
          name: "ghc-8.6.5 / lts-14.27"
          stack-yaml: stack-lts-14.27.yaml
      - stack-build/build-test-lint:
          name: "ghc-8.4.3 / lts-12.10"
          stack-yaml: stack-lts-12.10.yaml
      - stack-build/build-test-lint:
          name: "nightly"
          stack-yaml: stack-nightly.yaml
          stack-arguments: --resolver nightly
          hlint: false
          weeder: false
```

See [all examples](./src/examples/).

---

[LICENSE](./LICENSE) | [CHANGELOG](./CHANGELOG.md)
