# GitHub-CI-CD-with-aws-CodeBuild-CodePipeline-CloudFormation-template

### Référence de spécification de construction pour CodeBuild

> Si vous incluez un buildspec dans le cadre du code source, par défaut, le fichier buildspec doit être nommé buildspec.yml et placé à la racine de votre répertoire source.
> Utilisez un fichier buildspec différent pour différentes builds dans le même référentiel, comme buildspec_debug.yml et buildspec_release.yml.
> Stockez un fichier buildspec ailleurs qu'à la racine de votre répertoire source, tel que config/buildspec.yml ou dans un compartiment S3. Le compartiment S3 doit se trouver dans la même région AWS que votre projet de génération. Spécifiez le fichier buildspec à l'aide de son ARN (par exemple, arn:aws:s3:::my-codebuild-sample2/buildspec.yml).
> Vous ne pouvez spécifier qu'une seule spécification de construction pour un projet de génération, quel que soit le nom du fichier de spécification de construction.

> Pour remplacer le nom du fichier buildspec par défaut, l'emplacement ou les deux, effectuez l'une des opérations suivantes:
> Exécutez la commande create-project ou update-project de l'AWS CLI, en définissant la valeur buildspec sur le chemin d'accès au fichier buildspec alternatif par rapport à la valeur de la variable d'environnement intégrée CODEBUILD_SRC_DIR. Vous pouvez également faire l'équivalent avec l'opération de création de projet dans les kits SDK AWS. Pour plus d'informations, consultez Créer un projet de génération ou Modifier les paramètres d'un projet de génération.

> Dans un modèle AWS CloudFormation, définissez la propriété BuildSpec de Source dans une ressource de type AWS::CodeBuild::Project sur le chemin d'accès au fichier buildspec alternatif par rapport à la valeur de la variable d'environnement intégrée CODEBUILD_SRC_DIR. Pour plus d'informations, consultez la propriété BuildSpec dans la source du projet AWS CodeBuild dans le Guide de l'utilisateur AWS CloudFormation.

```
version: 0.2

run-as: Linux-user-name

env:
  shell: shell-tag
  variables:
    key: "value"
    key: "value"
  parameter-store:
    key: "value"
    key: "value"
  exported-variables:
    - variable
    - variable
  secrets-manager:
    key: secret-id:json-key:version-stage:version-id
  git-credential-helper: no | yes

proxy:
  upload-artifacts: no | yes
  logs: no | yes

batch:
  fast-fail: false | true
  # build-list:
  # build-matrix:
  # build-graph:

phases:
  install:
    run-as: Linux-user-name
    on-failure: ABORT | CONTINUE
    runtime-versions:
      runtime: version
      runtime: version
    commands:
      - command
      - command
    finally:
      - command
      - command
  pre_build:
    run-as: Linux-user-name
    on-failure: ABORT | CONTINUE
    commands:
      - command
      - command
    finally:
      - command
      - command
  build:
    run-as: Linux-user-name
    on-failure: ABORT | CONTINUE
    commands:
      - command
      - command
    finally:
      - command
      - command
  post_build:
    run-as: Linux-user-name
    on-failure: ABORT | CONTINUE
    commands:
      - command
      - command
    finally:
      - command
      - command
reports:
  report-group-name-or-arn:
    files:
      - location
      - location
    base-directory: location
    discard-paths: no | yes
    file-format: report-format
artifacts:
  files:
    - location
    - location
  name: artifact-name
  discard-paths: no | yes
  base-directory: location
  exclude-paths: excluded paths
  enable-symlinks: no | yes
  s3-prefix: prefix
  secondary-artifacts:
    artifactIdentifier:
      files:
        - location
        - location
      name: secondary-artifact-name
      discard-paths: no | yes
      base-directory: location
    artifactIdentifier:
      files:
        - location
        - location
      discard-paths: no | yes
      base-directory: location
cache:
  paths:
    - path
    - path

```
