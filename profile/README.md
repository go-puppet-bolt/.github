<p align="center"><img src="https://raw.githubusercontent.com/go-puppet-bolt/brand/main/social/go-puppet-bolt.png" alt="go-puppet-bolt" width="640"></p>

<h1 align="center">go-puppet-bolt</h1>
<p align="center"><strong>Puppet Bolt core in pure Go — inventory, tasks, YAML and Puppet-language plans, and SSH / WinRM / local transports.</strong></p>

<p align="center">
  🌐 <a href="https://go-puppet-bolt.github.io">Website</a> ·
  📚 <a href="https://go-puppet-bolt.github.io/docs/">Documentation</a>
</p>

<p align="center">
  <a href="https://go-puppet-bolt.github.io/docs/"><img alt="Docs" src="https://img.shields.io/badge/docs-mkdocs--material-4F46E5?style=flat-square"></a>
  <a href="https://github.com/go-puppet-bolt/bolt/blob/main/LICENSE"><img alt="License: BSD-3-Clause" src="https://img.shields.io/badge/license-BSD--3--Clause-blue?style=flat-square"></a>
  <img alt="Go 1.26.4+" src="https://img.shields.io/badge/go-1.26.4%2B-00ADD8?style=flat-square&logo=go&logoColor=white">
  <img alt="Coverage 100%" src="https://img.shields.io/badge/coverage-100%25-1a7f37?style=flat-square">
</p>

---

go-puppet-bolt is a pragmatic, pure-Go (CGO_ENABLED=0) port of the core of Puppet Bolt, the agentless orchestrator. It parses Bolt inventory, tasks and plans and runs them over pluggable transports — with no Ruby runtime and no cgo, so it cross-compiles to every 64-bit Go target and WebAssembly and links into a static binary. Inventory v2 resolves effective config / facts / vars through the group hierarchy and selects targets by name, alias, group or glob; tasks validate arguments against declared parameter types; YAML plans run an ordered sequence of task / command / script / eval / plan / resources / message steps; Puppet-language (.pp) plans run through go-puppet/puppet with their plan functions dispatched to real targets; apply blocks compile a catalog and report; and an Executor runs work across targets — over a host-local, a full SSH (x/crypto/ssh) or a full WinRM (WS-Management) transport — into a ResultSet. Its non-stdlib dependencies are all pure Go. 100% coverage, six arches.

## Repositories

| Repo | What it is |
|------|------------|
| [**bolt**](https://github.com/go-puppet-bolt/bolt) | the engine library |
| [**docs**](https://github.com/go-puppet-bolt/docs) | MkDocs Material documentation, versioned with [mike], served at [/docs/](https://go-puppet-bolt.github.io/docs/) |
| [**go-puppet-bolt.github.io**](https://github.com/go-puppet-bolt/go-puppet-bolt.github.io) | the Hugo landing page |
| [**brand**](https://github.com/go-puppet-bolt/brand) | logos and brand assets |

## Principles

- **Pure Go, zero cgo.** `CGO_ENABLED=0`; imports the Go standard library and a few pure-Go dependencies (<a href="https://github.com/go-ruby-yaml/yaml">go-ruby-yaml/yaml</a>, <a href="https://pkg.go.dev/golang.org/x/crypto/ssh">golang.org/x/crypto/ssh</a>, <a href="https://github.com/Azure/go-ntlmssp">go-ntlmssp</a>, <a href="https://github.com/go-puppet/puppet">go-puppet/puppet</a>). Cross-compiles to the
  six 64-bit Go targets (amd64, arm64, riscv64, loong64, ppc64le, s390x) and WebAssembly, linking into a static binary.
- **Faithful to Bolt's inventory v2, task metadata, YAML and Puppet-language plan shapes.**
- **An engine, not a service.** A small, stable Go API you embed — part of the
  pure-Go Puppet stack (siblings [go-facter](https://github.com/go-facter),
  [go-hiera](https://github.com/go-hiera), [go-pcore](https://github.com/go-pcore),
  [go-puppet](https://github.com/go-puppet)).
- **100% test coverage** including error branches, enforced as a CI gate.

BSD-3-Clause.

[mike]: https://github.com/jimporter/mike
