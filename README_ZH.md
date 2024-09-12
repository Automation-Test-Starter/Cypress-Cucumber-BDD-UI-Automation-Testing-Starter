<!-- markdownlint-disable MD041 -->
<!-- markdownlint-disable MD033 -->
<div align="right"><strong>🇨🇳中文</a></strong>  | <strong><a href="./README.md">🇬🇧English</strong></div>
<!-- markdownlint-disable MD041 -->
<!-- markdownlint-disable MD033 -->

# Cypress和Cucumber的WEB UI自动化测试快速启动项目

关于使用 Cypress和Cucumber进行 WEB UI 测试的快速启动项目介绍文档。

- [Cypress和Cucumber的WEB UI自动化测试快速启动项目](#cypress和cucumber的web-ui自动化测试快速启动项目)
  - [Cypress \& Cucumber \& BDD 介绍](#cypress--cucumber--bdd-介绍)
    - [Cypress 介绍](#cypress-介绍)
    - [Cucumber 介绍](#cucumber-介绍)
    - [BDD 介绍](#bdd-介绍)
  - [项目结构](#项目结构)
  - [项目依赖](#项目依赖)
  - [从 0 到 1 搭建 Cypress和Cucumber的WEB UI自动化测试项目](#从-0-到-1-搭建-cypress和cucumber的web-ui自动化测试项目)
    - [新建项目文件夹](#新建项目文件夹)
    - [项目初始化](#项目初始化)
    - [安装依赖](#安装依赖)
    - [Cypress 初始化](#cypress-初始化)
    - [cypress-cucumber-preprocessor配置](#cypress-cucumber-preprocessor配置)
    - [安装cypress-esbuild去修复 cypress 配置文件错误](#安装cypress-esbuild去修复-cypress-配置文件错误)
  - [](#)
  - [参考信息](#参考信息)

## Cypress & Cucumber & BDD 介绍

### Cypress 介绍

Cypress 是一个基于 JavaScript 的前端测试框架，专门用于为 Web 应用程序编写端到端测试（E2E）。它提供了简单、强大的 API，能够自动化浏览器中的操作，并进行功能测试、集成测试和单元测试。Cypress 的主要特点包括：

1. **自动化运行**：Cypress 可以模拟用户操作，如点击按钮、输入文本、导航等，适用于浏览器中的测试自动化。
2. **实时调试**：在测试过程中，Cypress 提供了一个交互式的调试工具，可以实时查看测试结果和应用程序状态。
3. **支持现代浏览器**：Cypress 支持多个主流浏览器，如 Chrome、Firefox 和 Edge。
4. **内置等待机制**：Cypress 自动处理异步操作，无需手动添加 `wait`，确保在适当的时机执行断言和操作。
5. **测试快照**：在每一步操作后，Cypress 都会拍下快照，方便调试和回溯错误。
6. **无服务依赖**：Cypress 直接在浏览器内运行，与应用程序的前端紧密集成，减少外部依赖。

总的来说，Cypress 是一个现代、用户友好的前端测试工具，特别适合用来验证 Web 应用的用户交互和界面逻辑。

官方网站: <https://www.cypress.io/>

### Cucumber 介绍

Cucumber 是一个广泛使用的行为驱动开发（BDD）工具，用于编写自动化测试。它通过自然语言（如英语）编写测试场景，使技术和非技术人员都能理解和参与测试流程。Cucumber 的主要特点包括：

1. **Gherkin 语法**：Cucumber 使用 Gherkin 语言编写测试用例，格式简单易懂，以 `Given-When-Then` 的格式描述行为。例子：
   - `Given` 描述初始状态
   - `When` 描述操作
   - `Then` 描述期望的结果
2. **跨平台支持**：Cucumber 支持多种编程语言，如 Java、JavaScript、Ruby、Python 等，因此适用于不同的开发环境。
3. **行为驱动开发（BDD）**：Cucumber 的核心是 BDD，即通过定义清晰的用户行为和期望的结果来推动开发，确保功能满足业务需求。
4. **可读性强**：由于测试用例是用自然语言编写的，业务人员、产品经理等非技术人员可以参与编写和理解测试。
5. **自动化测试**：Cucumber 将自然语言转化为可执行的代码，用于自动化测试，验证系统的行为与业务需求的匹配性。

总体而言，Cucumber 是一个强大的工具，能够有效促进开发团队和业务团队的协作，同时确保应用程序的功能与业务需求保持一致。

官方网站: <https://cucumber.io/>

### BDD 介绍

行为驱动开发（BDD，Behavior-Driven Development）是一种软件开发方法，它扩展了测试驱动开发（TDD）的理念，强调通过自然语言来描述软件的行为，使开发、测试和业务团队能够更好地协作。BDD 的主要目标是确保软件的功能与业务需求高度一致，减少沟通中的误解和信息差。

BDD 的核心概念包括：

1. **以行为为中心**：BDD 强调从用户和业务需求的角度来描述系统行为，而不是从技术实现的角度出发。这确保了软件开发紧密贴合用户需求。
   
2. **清晰的语言**：BDD 使用像 Gherkin 这样的自然语言来编写测试用例，通常以 `Given-When-Then` 的格式描述场景。这样，业务团队可以轻松理解并参与测试用例的编写。
   - `Given` 描述初始状态或前提条件。
   - `When` 描述执行的操作。
   - `Then` 描述期望的结果或系统反应。

3. **开发与测试紧密结合**：BDD 强调在开发过程的早期就定义并执行自动化测试，确保开发出的功能符合预期的业务行为。

4. **增强团队协作**：通过使用通用的自然语言，开发人员、测试人员和业务人员可以更紧密地协作，共同定义软件的功能和期望的行为。

5. **以用户故事为驱动**：BDD 通常基于用户故事，确保每个功能都从用户的需求和行为出发，避免过度的技术讨论或复杂实现。

BDD 能帮助团队确保每个功能都是基于真实的业务需求，减少返工，提升软件质量。

扩展阅读：<https://en.wikipedia.org/wiki/Behavior-driven_development>

## 项目结构

使用Cypress和Cucumber BDD进行Web UI自动化测试时，项目结构可以按照以下方式组织，以便于维护和扩展：

```
cypress-cucumber-project/
│
├── cypress/
│   ├── fixtures/
│   │   └── example.json           # 测试用的假数据
│   ├── e2e/
│   │   └── features/              # Cucumber特性文件目录
│   │       ├── login.feature      # 示例功能文件
│   │       └── other.feature
│   ├── plugins/
│   │   └── index.js               # 插件配置文件
│   └── support/
│       ├── commands.js            # 自定义Cypress命令
│       ├── index.js               # 支持文件
│       └── steps/                 # Cucumber步骤定义文件
│           ├── login.steps.js     # 示例步骤定义文件
│           └── other.steps.js
│
├── .gitignore                      # Git忽略文件
├── cypress.config.js              # Cypress配置文件
├── package.json                    # 项目依赖及脚本配置文件
└── README.md                       # 项目说明文档
```

主要文件和目录说明

1. **cypress/fixtures/**：存放测试用的测试数据文件，如JSON格式的数据文件。

2. **cypress/e2e/features/**：存放Cucumber的`.feature`文件，这些文件定义了测试场景和步骤。

3. **cypress/plugins/**：存放Cypress插件配置文件，例如`index.js`用于设置Cucumber与Cypress的集成。

4. **cypress/support/**：
   - `commands.js`：定义Cypress的自定义命令。
   - `index.js`：配置Cypress的全局设置和钩子。
   - `steps/`：存放Cucumber的步骤定义文件，这些文件实现了特性文件中定义的步骤。

5. **package.json**：项目依赖及脚本配置文件。
6. **README.md**：项目说明文档。
7. **.gitignore**：Git忽略文件。

## 项目依赖

> 我个人的电脑是M1的Mac，所以后续的环境配置和依赖相关都以Mac来做示例，其他的电脑同理。

需提前安装好以下环境

- node.js, demo 版本为 v22.18.0
- NPM, demo 版本为 v10.8.2
- Chrome浏览器或者Firefox浏览器，demo版本为最新版本

## 从 0 到 1 搭建 Cypress和Cucumber的WEB UI自动化测试项目

下面会从 0 到 1 搭建一个Cypress和Cucumber的WEB UI自动化测试项目，可参考 demo 项目：<https://github.com/Automation-Test-Starter/Cypress-Cucumber-BDD-Demo.git>

### 新建项目文件夹

```bash
mkdir Cypress-Cucumber-BDD-Demo
```

### 项目初始化

```bash
// 进入项目文件夹下
cd Cypress-Cucumber-BDD-Demo
// nodejs 项目初始化
npm init -y
```
>项目初始化的时候会有一些自定义项目的提示，直接按回车保存默认即可。后续也可以在`package.json`中添加自定义配置。

### 安装依赖

```bash
// 安装 cypress
npm install cypress --save-dev
// 安装 cucumber
npm install @badeball/cypress-cucumber-preprocessor --save-dev
```

### Cypress 初始化

```bash
// cypress 初始化
npx cypress init
```

根据提示进行初始化即可

### cypress-cucumber-preprocessor配置

1. 重命名`cypress.config.js`文件，命名为`cypress.config.ts`：

2. 更改`cypress.config.ts`文件内容如下：

```ts
import { defineConfig } from "cypress";
import createBundler from "@bahmutov/cypress-esbuild-preprocessor";
import { addCucumberPreprocessorPlugin } from "@badeball/cypress-cucumber-preprocessor";
import createEsbuildPlugin from "@badeball/cypress-cucumber-preprocessor/esbuild";

export default defineConfig({
  e2e: {
    specPattern: "**/*.feature",
    async setupNodeEvents(
      on: Cypress.PluginEvents,
      config: Cypress.PluginConfigOptions
    ): Promise<Cypress.PluginConfigOptions> {
      // This is required for the preprocessor to be able to generate JSON reports after each run, and more,
      await addCucumberPreprocessorPlugin(on, config);

      on(
        "file:preprocessor",
        createBundler({
          plugins: [createEsbuildPlugin(config)],
        })
      );

      // Make sure to return the config object as it might have been modified by the plugin.
      return config;
    },
  },
});
```

扩展阅读：<hhttps://github.com/badeball/cypress-cucumber-preprocessor/blob/master/docs/quick-start.md>

### 安装cypress-esbuild去修复 cypress 配置文件错误

```bash
// 安装cypress-esbuild修复找不到cypress-esbuild-preprocessor模块引用的报错

npm install @bahmutov/cypress-esbuild-preprocessor --save-dev
```

- 参考文档：https://github.com/badeball/cypress-cucumber-preprocessor/blob/master/docs/quick-start.md


##

## 参考信息

- Cypress <https://www.cypress.io/>

- Cucumber <https://cucumber.io/>

- BDD：<https://en.wikipedia.org/wiki/Behavior-driven_development>

- Automation Testing Starter <https://github.com/Automation-Test-Starter>

- Cypress-Cucumber-BDD-Demo <https://github.com/Automation-Test-Starter/Cypress-Cucumber-BDD-Demo.git>