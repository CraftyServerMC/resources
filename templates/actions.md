# Templates for Github Actions
This document contains a few templates for Github Actions that might be needed for module repositories. They should be stored in `.github/workflows`.
## Contents
1. [Maven build test](#maven-test)
2. [Dynamic readme](#dynamic-readme)
## Maven build test<a id='maven-test'></a>
Stored in `maven.yml'
```YML
# This workflow will build a Java project with Maven, and cache/restore any dependencies to improve the workflow execution time
# For more information see: https://help.github.com/actions/language-and-framework-guides/building-and-testing-java-with-maven

name: Java CI with Maven

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Set up JDK 11
      uses: actions/setup-java@v2
      with:
        java-version: '11'
        distribution: 'temurin'
        cache: maven
    - name: Build with Maven
      run: mvn -X install --file pom.xml
```
## Dynamic readme<a id='dynamic-readme'></a>
Stored in `dynamic-readme.yml`
```YML
name: Dynamic Template

on:
  push:
    branches:
      - main
	schedule:
      - cron:  '* 0 * * *'
  workflow_dispatch:

jobs:
  update_templates:
    name: "Update Markdown Templates"
    runs-on: ubuntu-latest
    steps:
      - name: "📥  Fetching Repository Contents"
        uses: actions/checkout@main

      - name: "💾  Github Repository Metadata"
        uses: varunsridharan/action-repository-meta@main
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

      - name: "💫  Dynamic Template Render"
        uses: varunsridharan/action-dynamic-readme@main
        with:
          GLOBAL_TEMPLATE_REPOSITORY: CraftyServerMC/resources/templates/dynamic-readme-templates
          files: |
            README.md
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```