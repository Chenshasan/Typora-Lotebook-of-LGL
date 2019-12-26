## jhipster环境配置

- 安装java

- 安装git

- 安装nodejs

  1. nodejs官网下载数据
  2. nodejs安装（勾选add to path）
  3. node -v查看是否安装成功
  4. npm -v查看是否安装成功

- Jhisper安装，因为要使用vue版本，因此jhisper安装使用

  $ npm install -g generator-jhipster@6.4.1命令

- 安装jhipster——vueNPM包

  $ npm install -g generator-jhipster-vuejs

- 将vue链接至当前项目的依赖(管理员权限)

  $ npm link generator-jhipster-vuejs

- 生成vue-JS前后端分离项目（管理员权限）

  $ jhipster -d --blueprint vuejs

- 导入依赖（管理员权限）

  $ npm run webpack:build 



## Running local Blueprint version for development

During development of blueprint, please note the below steps. They are very important.

1. Clone the projects

You'll probably need the current master of **generator-jhipster** :

- fork generator-jhipster: `https://github.com/jhipster/generator-jhipster/fork`
- clone locally your fork: `git clone https://github.com/<your_username>/generator-jhipster`
- `cd generator-jhipster`
- `git remote add upstream https://github.com/jhipster/generator-jhipster`
- so you'll be able to update regularly your fork, using `git fetch upstream && git checkout master && git rebase upstream/master`
- `npm ci`
- `npm link`

Then, about **jhipster-vuejs** :

- fork jhipster-vuejs: `https://github.com/jhipster/jhipster-vuejs/fork`
- clone locally your fork: `git clone https://github.com/<your_username>/jhipster-vuejs`
- `cd jhipster-vuejs`
- `git remote add upstream https://github.com/jhipster/jhipster-vuejs`
- so you'll be able to update regularly your fork, using `git fetch upstream && git checkout master && git rebase upstream/master`
- `npm ci`
- `npm link`
- `npm link generator-jhipster`


2. Create a new folder for the app to be generated and link JHipster and your blueprint there

```bash
mkdir my-app
cd my-app
npm link generator-jhipster-vuejs
jhipster -d --blueprints vuejs
```



#### bootstrap-vue项目初始化

- 依赖导入：如果依赖导入过程中断可以通过file-invaild cache and restart来重新导入
- 前端项目开始：
  - npm install
  - npm intall webpack:build
  - npm start
- 可以通过npm audit fix来进行部分修复（作用不好说）
- 记得开后端项目（整体项目结构为通过后端直接run整个app文件，当配置完成后直接run app即可）


