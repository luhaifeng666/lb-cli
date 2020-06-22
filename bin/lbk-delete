#! /usr/bin/env node

const inquirer = require('inquirer')
const chalk = require('chalk')
const fs = require('fs')
const tplObj = require(`${__dirname}/../template`)

let questions = [
  {
    name: 'name',
    message: '请输入需要删除的模板名称',
    validate (val) {
      if (!val) {
        return 'Name is required!'
      } else if (!tplObj[val]) {
        return 'Template does not exist!'
      } else {
        return true
      }
    }
  }
] 
  
inquirer
  .prompt(questions).then(answer => {
    const {name} = answer
    delete tplObj[name]

    fs.writeFile(`${__dirname}/../template.json`, JSON.stringify(tplObj), 'utf-8', err => {
      if (err) {
        console.log(chalk.red(`Error: ${err.message}`))
        return false
      } else {
        console.log('\n')
        console.log(chalk.green('Deleted successfully!\n'))
        console.log(chalk.grey('The latest template list is: \n'))
        console.log(tplObj)
        console.log('\n')
      }
    })
  })