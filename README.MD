#Configuração do Sequelize
O arquivo .sequelizerc irá determinar o caminho quando iniciarmos o sequelize com o comando npx ou yarn sequelize init.

yarn add nodemon sequelize-cli sucrase prettier eslint eslint-config-prettier eslint-plugin-prettier -D

#Nodemon e Sucrase
Para que possamos usar o Import/Export no node, iremos utilizar o sucrase para fazer a configuração,

#Database - Utilizando o Postgres e o Sequelize

require('dotenv/config');

module.exports = {
dialect: process.env.DB_DIALECT || 'postgres',
host: process.env.DB_HOST || 'localhost',
username: process.env.DB_USER,
password: process.env.DB_PASS,
database: process.env.DB_NAME,
logging: false,
define: {
timestamps: true,
underscored: true,
undercoredAll: true,
},
};

#Prettier e Eslint
Para a configuração da estilização do código será utilizado o eslint com o prettier

#Criando migrations no sequelize

yarn sequelize migration:create --name=

#Migration de User padrão
id: {
type: Sequelize.INTEGER,
primaryKey: true,
autoIncrement: true,
allowNull: false,
},
name: {
type: Sequelize.STRING,
allowNull: false,
},
email: {
type: Sequelize.STRING,
allowNull: false,
},
password_hash: {
type: Sequelize.STRING,
allowNull: false,
set: value =>
crypto.createHash('md5)
.update(value)
.digest('hex')
},
created_at: {
type: Sequelize.DATE,
allowNull: false,
},
updated_at: {
type: Sequelize.DATE,
allowNull: false,
},
