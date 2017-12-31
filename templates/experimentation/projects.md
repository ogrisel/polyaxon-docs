A `Project` in Polyaxon is very similar to a project in github,
it aims at organizing your efforts to solve a specific problem.

## Create a project

To create a project, you can both use the Polyaxon Dashboard or the Polyaxon CLI.

The projects consist of a required argument `name` and an optional `description`.

The projects could be `public` (default behaviour) or set to private, in that case you only, and `superusers` can access the project.

Public project are visible to everyone as read only mode, and read/write mode to the `owner` and `superuser`.

??? note "More permissions and roles"
    More permissions and roles will be available, when be available when add organizations.
    If you want to be notified when we release this feature, please subscribe to be receive our progress.


??? Tip "Only the creator and superusers can create experiment groups and experiments"
    Even if you set your project to `public`, only you, i.e. the creator, and the superuser,
    will be able to run experiments in this project.
    `public` only gives read access to other users in your team.


### Creating a project with the dashboard

### Creating a project with the CLI

```bash
$ polyaxon project create --name=mnist --description='Classification of handwritten images.'
```

!!! info
    For more details about this command please run `polyaxon project create --help`,
    or check the [command reference]()

The project is created with public, to make it private please add `--private`

## Initializing a project

After creating a project, you can start your experimentation process,
and the first step is to initialize a workspace for your project on your workstation.

```bash
$ mkdir mnsit
$ cd mnist

$ polyaxon init mnist

Project `mnist` was initialized and Polyaxonfile was created successfully `polyaxonfile.yml`
```

When a project is initialized, polyaxon creates a default `.polyaxonignore`,
you can customize it to ignore the files that you don't want to upload.

Now you can add some code to your project.

Before doing anything you must update the default polyaxonfile to tell polyaxon how to run your code

```bash
$ vi polyaxonfile.yml
```

## Upload code for this project

Upload your to polyaxon to commit this current version.

```bash
$ vi train.py
...

$ polyaxon upload
[================================] 675/675 - 00:00:00

Files uploaded.
```


You are ready now to run experiment, please go to [experiment groups](experiment_groups)
if you want to do a hyperparameters search and run multiple experiments concurrently.

Otherwise go to [experiments](experiments) if you want to run a single experiment.