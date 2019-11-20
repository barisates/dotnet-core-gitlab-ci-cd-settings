# dotnet-core-gitlab-ci-cd-settings
GitLab CI / CD settings for displaying test coverage report output in ASP.NET Core applications.

### Coverlet

We use Coverlet for code coverage report. It allows us to integrate GitLab  CI / CD by displaying the report output on the console. For detailed knowledgeable; [Coverlet](https://github.com/tonerdo/coverlet "Coverlet").

**Coverlet should only be added to your test projects!**

*Latest stable version:* [![NuGet](https://img.shields.io/nuget/v/coverlet.msbuild.svg)](https://www.nuget.org/packages/coverlet.msbuild)

```
dotnet add package coverlet.msbuild
```
**Coverlet output on Gitlab CI / CD:**

![Coverlet output on Gitlab CI / CD](http://barisates.com/git/ci-cd/coverlet-console.jpg "Coverlet output on Gitlab CI / CD")

### GitLab CI / CD
To manage the GitLab CI / CD process, we need knowledge of the project's code coverage report about testing. After adding the Coverlet package to our test project, we make GitLab CI / CD settings.

**Test stage script for `.gitlab-ci.yml` file:**
```yml
test:
  stage: test
  script:
    - dotnet test /p:CollectCoverage=true
```

**Test coverage parsing:**
```regex
Total[^|]*\|[^|]*\s+([\d\.]+)
```

**Coverage report badge:**

![Coverage report badge](http://barisates.com/git/ci-cd/badge.jpg "Coverage report badge")