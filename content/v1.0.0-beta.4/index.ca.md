---
draft: false
aliases: ["/ca/"]
---

# Commits Convencionals 1.0.0-beta.4

## Breu Resum

L'especificació de _Commits_ Convencionals és una convenció lleugera per a la part superior dels missatges de _commit_.
Proporciona un conjunt de regles senzilles per a crear un històric explícit dels _commits_, el que facilita la creació d’eines automatitzades per sobre.
Aquesta convenció coincideix amb [SemVer](http://semver.org),
descrivint les _features_, _fixes_, i els _breaking changes_ fets en els missatges de _commit_.

El missatge de _commit_ ha d’estar estructurat de la manera següent:

---

```
<tipus>[àmbit optional]: <descripció>

[cos optional]

[peu optional]
```
---

<br />
El _commit_ conté els següents elements estructurals, per comunicar la intenció amb qui utilitzi la vostra llibreria:


1. **fix:** un _commit_ de tipus `fix` soluciona un problema (_bug_) en el codi (això es correlaciona amb [`PATCH`](http://semver.org/#summary) en el versionat semàntic).
1. **feat:** un _commit_ de tipus `feat` introdueix una nova funcionalitat (_feature_) al codi (això es correlaciona amb [`MINOR`](http://semver.org/#summary) en el versionat semàntic).
1. **BREAKING CHANGE:** un _commit_ que te el text `BREAKING CHANGE:` al principi del cos o del peu opcional introdueix un trencament de la compatibilitat en l'ús de l'API
(es correlaciona amb [`MAJOR`](http://semver.org/#summary) en el versionat semàntic).
Un BREAKING CHANGE pot formar part de _commits_ de qualsevol _tipus_.
1. Altres: tipus de _commit_ diferents de `fix:` i `feat:` són permesos, per exemple [@commitlint/config-conventional](https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional) (basat en [la Convenció d'Angular](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines)) recomana `chore:`, `docs:`, `style:`, `refactor:`, `perf:`, `test:`, i altres.

També recomanem `improvement` per a _commits_ que milloren una actual implementació sense afegir una nova funcionalitat (feature) o resoldre un problema (fixing a bug).
Tingueu en compte que aquests tipus no estan obligats per l’especificació dels Commits Convencionals i no tenen cap efecte implícit en la versió semàntica (tret que incloguin un BREAKING CHANGE).
<br />
Es pot proporcionar un àmbit a un tipus de _commit_, per proporcionar informació contextual addicional i es troba dins dels parèntesis, per exemple, `feat(parser): afegir capacitat per analitzar matrius`.

## Exemples

### Missatge d'un _commit_ amb una descripció i un _breaking change_ en el cos
```
feat: permetre l'objecte de configuració proporcionat per estendre altres configuracions

BREAKING CHANGE: la clau `extends` en el fitxer de configuració s’utilitza ara per ampliar altres fitxers de configuració
```

### Missatge d'un commit amb la opció `!` per cridar l'atenció al _breaking change_
```
chore!: eliminar el Node 6 des de la matriu de proves

BREAKING CHANGE: eliminant Node 6 que a l'abril arriba al seu final de vida
```

### Missatge d'un _commit_ sense cos
```
docs: ortografia correcta del CHANGELOG
```

### Missatge d'un _commit_ amb un àmbit
```
feat(lang): afegir llenguatge polit
```

### Missatge d'un _commit_ per a un _fix_ fent servir el número d'_issue_ (optional)
```
fix: corregir errors tipogràfics menors al codi

vegeu el issue per més informació sobre els errors tipogràfics corregits

Es tanca el issue #12
```

## Especificació

Les paraules "HAVER DE" (“MUST”), "NO HA DE SER" (“MUST NOT”), "NECESSARI" (“REQUIRED”), “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” en aquest document s'han d'interpretar com es descriu al [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

1. Commits MUST be prefixed with a type, which consists of a noun, `feat`, `fix`, etc., followed
  by an OPTIONAL scope, and a REQUIRED terminal colon and space.
1. The type `feat` MUST be used when a commit adds a new feature to your application or library.
1. The type `fix` MUST be used when a commit represents a bug fix for your application.
1. A scope MAY be provided after a type. A scope MUST consist of a noun describing a
  section of the codebase surrounded by parenthesis, e.g., `fix(parser):`
1. A description MUST immediately follow the space after the type/scope prefix.
The description is a short summary of the code changes, e.g., _fix: array parsing issue when multiple spaces were contained in string._
1. A longer commit body MAY be provided after the short description, providing additional contextual information about the code changes. The body MUST begin one blank line after the description.
1. A footer of one or more lines MAY be provided one blank line after the body. The footer MUST contain meta-information
about the commit, e.g., related pull-requests, reviewers, breaking changes, with one piece of meta-information
per-line.
1. Breaking changes MUST be indicated at the very beginning of the body section, or at the beginning of a line in the footer section. A breaking change MUST consist of the uppercase text BREAKING CHANGE, followed by a colon and a space.
1. A description MUST be provided after the `BREAKING CHANGE: `, describing what has changed about the API, e.g., _BREAKING CHANGE: environment variables now take precedence over config files._
1. Types other than `feat` and `fix` MAY be used in your commit messages.
1. The units of information that make up conventional commits MUST NOT be treated as case sensitive by implementors, with the exception of BREAKING CHANGE which MUST be uppercase.
1. A `!` MAY be appended prior to the `:` in the type/scope prefix, to further draw attention to breaking changes. `BREAKING CHANGE: description` MUST also be included in the body
or footer, along with the `!` in the prefix.

## Per què utilitzar _Commits_ Convencionals?

* Et permet la generació automatica dels CHANGELOGs.
* Et determina automàticament el versionat semàntic (basat en els tipus de _commits_ realitzats).
* Comunica la naturalesa dels canvis als companys d’equip, al públic i als altres grups d’interès.
* Et permet activar processos de creació i publicació.
* Facilita que la gent contribueixi als vostres projectes, ja que els permet explorar
   un historial de _commits_ més estructurat.

## Preguntes freqüents

### Com he de tractar els missatges de _commit_ en la fase de desenvolupament inicial?

Us recomanem que procediu com si ja hagueu llançat el producte. Normalment *algú*, encara que sigui els vostres desenvolupadors de programari, està utilitzant el vostre programari. Ells voldran saber què és el que està arreglat, què es trenca, etc.

### Els tipus al títol del _commit_ s'escriuen en majúscules o minúscules?

Qualsevol opció és correcta, però el millor és ser coherent.

### Què faig si el _commit_ s'ajusta a més d'un dels tipus de _commit_?

Torneu enrere i feu múltiples _commits_ sempre que sigui possible. Una part del benefici dels _Commits_ Convencionals és la seva capacitat per conduir-nos a fer _commits_ i PRs més organitzats.

### Això no desanima el desenvolupament ràpid i la iteració ràpida?

Desanima moures ràpid de manera desorganitzada. Us ajuda a poder moure ràpidament a llarg termini a través de múltiples projectes amb col·laboradors variats.

### Els _Commits_ Convencionals poden portar els desenvolupadors a limitar el tipus de _commits_ que fan perquè pensaran en els tipus proposats?

Conventional Commits encourages us to make more of certain types of commits such as fixes. Other than that, the flexibility of Conventional Commits allows your team to come up with their own types and change those types over time.

### How does this relate to SemVer?

`fix` type commits should be translated to `PATCH` releases. `feat` type commits should be translated to `MINOR` releases. Commits with `BREAKING CHANGE` in the commits, regardless of type, should be translated to `MAJOR` releases.

### How should I version my extensions to the Conventional Commits Specification, e.g. `@jameswomack/conventional-commit-spec`?

We recommend using SemVer to release your own extensions to this specification (and
encourage you to make these extensions!)

### What do I do if I accidentally use the wrong commit type?

#### When you used a type that's of the spec but not the correct type, e.g. `fix` instead of `feat`

Prior to merging or releasing the mistake, we recommend using `git rebase -i` to edit the commit history. After release, the cleanup will be different according to what tools and processes you use.

#### When you used a type *not* of the spec, e.g. `feet` instead of `feat`

In a worst case scenario, it's not the end of the world if a commit lands that does not meet the conventional commit specification. It simply means that commit will be missed by tools that are based on the spec.

### Do all my contributors need to use the conventional commit specification?

No! If you use a squash based workflow on Git lead maintainers can clean up the commit messages as they're merged—adding no workload to casual committers.
A common workflow for this is to have your git system automatically squash commits from a pull request and present a form for the lead maintainer to enter the proper git commit message for the merge.

## Quant a

L'especificació dels _Commits_ Conventionals està inspirada, i basant-se molt, en la [Angular Commit Guidelines](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines).

El primer esborrany d’aquesta especificació s’ha escrit en col·laboració amb algunes de les persones que contribueixen a:

* [conventional-changelog](https://github.com/conventional-changelog/conventional-changelog): un conjunt d’eines per analitzar els missatges de _commits_ convencionals de les històries git.
* [bumped](https://bumped.github.io): una eina per alliberar programari que faciliti realitzar accions abans i després de llançar una nova versió del vostre programari.
* [unleash](https://github.com/netflix/unleash): una eina per automatitzar el cicle de vida d’edició i publicació de programari.
* [lerna](https://github.com/lerna/lerna): una eina per gestionar monorepos, que va sorgir del projecte Babel.

## Eines per _Commits_ Convencionals

* [php-commitizen](https://github.com/damianopetrungaro/php-commitizen): a tool built to create commit messages following the Conventional Commit specs. 
Configurable and usable for PHP projects as a composer dependency or usable globally for non-PHP projects.
* [conform](https://github.com/autonomy/conform): a tool that can be used to enforce policies on git repositories, including conventional commits.
* [standard-version](https://github.com/conventional-changelog/standard-version): Automatic versioning and CHANGELOG management, using GitHub's new squash button and the recommended Conventional Commits workflow.

## Projectes que fan servir _Commits_ Convencionals

* [yargs](https://github.com/yargs/yargs): everyone's favorite pirate themed command line argument parser.
* [istanbuljs](https://github.com/istanbuljs/istanbuljs): a collection of open-source tools and libraries for adding test coverage to your JavaScript tests.
* [uPortal-home](https://github.com/UW-Madison-DoIT/angularjs-portal) and [uPortal-application-framework](https://github.com/UW-Madison-DoIT/uw-frame): Optional supplemental user interface enhancing [Apereo uPortal](https://www.apereo.org/projects/uportal).
* [massive.js](https://github.com/dmfay/massive-js): A data access library for Node and PostgreSQL.
* [electron](https://github.com/electron/electron): Build cross-platform desktop apps with JavaScript, HTML, and CSS.
* [scroll-utility](https://github.com/LeDDGroup/scroll-utility): A simple to use scroll utility package for centering elements, and smooth animations
* [Blaze UI](https://github.com/BlazeUI/blaze): Framework-free open source UI toolkit.
* [Monica](https://github.com/monicahq/monica): An open source personal relationship management system.
* [mhy](https://mhy.js.org): 🧩 A zero-config, out-of-the-box, multi-purpose toolbox and development environment.

[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)

_vols veure el teu projecte en aquesta llista?_ [envia un pull request](https://github.com/conventional-changelog/conventionalcommits.org/pulls).
