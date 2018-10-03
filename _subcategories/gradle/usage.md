# Usage

## Table of contents

- Insallation
- Upgrade





## Upgrade

If you are an Android Developer, you might be using gradle wrapper. (bla bla)

If you just want to upgrade your machine global environment Gradle version, you could run

```
brew upgrade gradle
```

if you are running brew

Althouugh the easiest way is to create a wrapper for the specific project (it will create the appropiate files), but using:
```
gradle wrapper
```
so every person working on that specific project will use the same Gradle version.