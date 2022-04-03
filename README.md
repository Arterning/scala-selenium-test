# Scala 安装

使用 idea scala 的插件安装 scala 比较方便

# 安装 chrome driver

通过一条命令安装 ChromeDriver 是可以的。您可以使用 Chocolatey，这是一个 Windows 上的包管理工具，通过一条命令来安装 ChromeDriver。

首先，请确保已经安装了 Chocolatey。如果没有，请参考安装说明：https://chocolatey.org/install

然后，打开命令提示符并输入以下命令：

`choco install chromedriver`

这条命令将自动下载并安装 ChromeDriver，并将其配置到环境变量中，因此您可以直接在命令提示符中使用 ChromeDriver。

如果您想要安装特定版本的 ChromeDriver，请使用以下命令：

`choco install chromedriver --version=<version>`

`choco uninstall chromedriver`

# selenium 是什么

Selenium 是一个自动化测试工具，用于测试网页和 Web 应用程序。它提供了丰富的 API，使开发人员能够编写脚本来模拟用户操作，如点击链接、输入表单数据等。通过使用 Selenium，开发人员可以确保 Web 应用程序的功能正确，并且能够自动化地重复进行测试。

Selenium 支持多种编程语言，如 Java、Python、C# 等，并且支持多种浏览器，如 Chrome、Firefox、Internet Explorer 等。

它还提供了 Selenium Grid，这是一种分布式测试环境，可以在多台计算机上并行运行测试。这对于测试多个浏览器和多个操作系统的配置非常有用。

# Scala Test

ScalaTest 是一个 Scala 语言的测试框架。它提供了一组功能强大的 API，以帮助开发人员编写和运行单元测试、功能测试、性能测试等。

ScalaTest 使用了表示式语言，使得代码更加简洁易读，同时也提供了丰富的断言和断定，用于测试结果的验证。它还支持并行测试，可以帮助加快测试速度。

ScalaTest 还支持多种测试风格，如 FunSuite、FlatSpec、WordSpec、PropSpec 等，这使得开发人员可以根据需要选择最适合的测试风格。

此外，ScalaTest 还提供了许多插件，如 ScalaCheck、ScalaMock 等，以帮助开发人员实现测试驱动开发（TDD）和行为驱动开发（BDD）等。

总的来说，ScalaTest 是一个功能强大、易于使用的 Scala 测试框架，适用于各种类型的测试。

来看一个简单例子

```scala
import org.scalatest._

class MySpec extends FlatSpec with Matchers {
  "A Stack" should "pop values in last-in-first-out order" in {
    val stack = new Stack[Int]
    stack.push(1)
    stack.push(2)
    stack.pop() should be (2)
    stack.pop() should be (1)
  }

  it should "throw NoSuchElementException if an empty stack is popped" in {
    val emptyStack = new Stack[Int]
    a [NoSuchElementException] should be thrownBy {
      emptyStack.pop()
    }
  }
}

```

# Selenium-ScalaTest

A Simple template repository to showcase usage of Selenium tests using ScalaTest framework with Page Object Pattern
way of organizing tests.

ScalaTest is the most flexible testing tool in the Scala ecosystem. With ScalaTest, you can test Scala,
Scala.js (JavaScript), and Java code. ScalaTest includes a DSL for writing browser-based tests using Selenium.

To understand about the folder structure of this Scala project, please refer this [blog](http://allaboutscala.com/tutorials/chapter-1-getting-familiar-intellij-ide/intellij-project-structure-getting-started-scala-project/) post

### Build tool

We use `sbt` as a build tool. It is an open-source build tool for Scala and Java projects, similar to
Apache's Maven and Ant.

Please follow the [instructions](https://www.scala-sbt.org/1.x/docs/Setup.html) to install `sbt` on your machine
and available in PATH

Just like in any other project, the first step is to add selenium dependency to the build file(sbt) using

```scala
libraryDependencies += "org.seleniumhq.selenium" % "selenium-java" % "3.141.59" % "test"
```

### Source

To demonstrate the implementation of page object pattern we use two application here, Google Search and
Spree Demo website. Note that we don't use Page Factory pattern here as its going to be deprecated.

The tests are located [here](/src/test/scala/tests) and the pageobject classes are located [here](src/test/scala/pages)

### Execute Tests

`sbt test`

### IDE

You could use [Scala for Eclipse](http://scala-ide.org/) or IntelliJ Idea Community with Scala [plugin](https://plugins.jetbrains.com/plugin/1347-scala)

References:

- [Scala School](https://twitter.github.io/scala_school/)
- [sbt-reference](https://www.scala-sbt.org/1.x/docs/index.html)
- [Scala Test](http://www.scalatest.org/)
