<!--- Copyright (C) 2009-2013 Typesafe Inc. <http://www.typesafe.com> -->
# Building Play from source

To benefit from the latest improvements and bug fixes after the initial beta release, you may want to compile Play from source. You’ll need a [Git client](http://git-scm.com/) to fetch the source.

## Grab the source
From the shell, first checkout the Play source:

```bash
$ git clone git://github.com/playframework/playframework.git
```

Then go to the `playframework/framework` directory and launch the `build` script to enter the sbt build console:

```bash
$ cd playframework/framework
$ ./build
> publish-local
```

> Note that you don’t need to install sbt yourself: Play embeds its own version.

If you want to make changes to the code you can use `publish-local` to rebuild the framework.

## Build the documentation

Documentation is available at playframework/documentation as Markdown files.  To see HTML, run the following:

```bash
$ cd playframework/documentation
$ ./build run
```

To see documentation at [http://localhost:9000/@documentation](http://localhost:9000/@documentation)

For more details on developing the Play documentation, see the [[Documentation Guidelines|Documentation]].

## Run tests

You can run basic tests from the sbt console using the `test` task:

```
> test
```

We are also using several Play applications to test the framework. To run this complete test suite, use the `runtests` script:

```
$ ./runtests
```

## Use in projects

Creating projects using the Play version you have built from source works much the same as a regular Play application.

export PATH=$PATH:<projdir>/

If you have an existing Play application that you are upgrading, please add

```
resolvers ++= Seq(
  ...
  Resolver.file("Local Repository", file("<projdir>/repository/local"))(Resolver.ivyStylePatterns),
  ...
)

addSbtPlugin("com.typesafe.play" % "sbt-plugin" % "2.3-SNAPSHOT")
```

to project/plugins.sbt. 

## Using Code in Eclipse

You can find at [Stackoverflow](http://stackoverflow.com/questions/10053201/how-to-setup-eclipse-ide-work-on-the-playframework-2-0/10055419#10055419) some information how to setup eclipse to work on the code.
