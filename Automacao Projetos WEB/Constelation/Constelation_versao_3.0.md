## Nova Versão | Constellation:

```bash
#!/bin/bash

echo "======================================"
echo "WELCOME!"
echo "CONSTELLATIONS ENTERPRISE EDITION 2.0 | TEST CLI"
echo "Pay one Coffee | Help For All Dev's"
echo "CLI MADE IN BRASIL"
echo "CLI for Dev's WEB"
echo "======================================"

read -p "Digite o nome do seu projeto: " PROJECT_NAME

# Diretórios base
BASE_DIR="$PROJECT_NAME"
BACKEND_DIR="$BASE_DIR/Backend"
FRONTEND_DIR="$BASE_DIR/Frontend"
MOBILE_DIR="$BASE_DIR/Mobile_React_Native"
JSON_DIR="$BASE_DIR/Json_Teste"
DATABASE_DIR="$BASE_DIR/Data_Base_tests"
TESTS_DIR="$BASE_DIR/Tests"

mkdir -p "$BACKEND_DIR" "$FRONTEND_DIR" "$MOBILE_DIR" "$JSON_DIR" "$DATABASE_DIR" "$TESTS_DIR"

echo "Projeto criado em: $BASE_DIR"

# ===============================
# Função para criar arquivos
# ===============================
cria_arquivo() {
    local file_path="$BACKEND_DIR/$1"
    mkdir -p "$(dirname "$file_path")"
    touch "$file_path"
    echo "Arquivo criado: $file_path"
}

# ===============================
# Backends
# ===============================
backend_js() {
    for file in \
        app/controller/HomeController.js \
        app/controller/UserController.js \
        app/controller/AuthController.js \
        app/model/UserModel.js \
        app/model/ProductModel.js \
        app/model/AuthModel.js \
        app/service/UserService.js \
        app/service/AuthService.js \
        app/service/ProductService.js \
        app/repository/UserRepository.js \
        app/repository/ProductRepository.js \
        app/middleware/auth.middleware.js \
        app/middleware/error.middleware.js \
        app/entity/UserEntity.js \
        app/entity/ProductEntity.js \
        app/dto/UserDTO.js \
        app/dto/AuthDTO.js \
        app/config/database.config.js \
        app/config/server.config.js \
        app/config/env.config.js \
        app/helpers/logger.helper.js \
        app/helpers/validator.helper.js \
        app/utils/crypto.util.js \
        app/utils/response.util.js \
        app/routes/index.routes.js \
        app/routes/user.routes.js \
        app/routes/auth.routes.js
    do
        cria_arquivo "$file"
    done
}

backend_ts() {
cat <<EOF > "$BACKEND_DIR/tsconfig.json"
{
  "compilerOptions": {
    "target": "ES6",
    "module": "CommonJS",
    "strict": true,
    "rootDir": "./app",
    "outDir": "./dist",
    "esModuleInterop": true
  }
}
EOF

    for file in \
        app/controller/HomeController.ts \
        app/controller/UserController.ts \
        app/controller/AuthController.ts \
        app/model/UserModel.ts \
        app/model/ProductModel.ts \
        app/model/AuthModel.ts \
        app/service/UserService.ts \
        app/service/AuthService.ts \
        app/service/ProductService.ts \
        app/repository/UserRepository.ts \
        app/repository/ProductRepository.ts \
        app/middleware/auth.middleware.ts \
        app/middleware/error.middleware.ts \
        app/entity/UserEntity.ts \
        app/entity/ProductEntity.ts \
        app/dto/UserDTO.ts \
        app/dto/AuthDTO.ts \
        app/config/database.config.ts \
        app/config/server.config.ts \
        app/config/env.config.ts \
        app/helpers/logger.helper.ts \
        app/helpers/validator.helper.ts \
        app/utils/crypto.util.ts \
        app/utils/response.util.ts \
        app/routes/index.routes.ts \
        app/routes/user.routes.ts \
        app/routes/auth.routes.ts
    do
        cria_arquivo "$file"
    done
}

backend_php() {
    for file in \
        app/controller/HomeController.php \
        app/controller/UserController.php \
        app/controller/AuthController.php \
        app/model/UserModel.php \
        app/model/ProductModel.php \
        app/model/AuthModel.php \
        app/service/UserService.php \
        app/service/AuthService.php \
        app/service/ProductService.php \
        app/repository/UserRepository.php \
        app/repository/ProductRepository.php \
        app/middleware/auth.middleware.php \
        app/middleware/error.middleware.php \
        app/entity/UserEntity.php \
        app/entity/ProductEntity.php \
        app/dto/UserDTO.php \
        app/dto/AuthDTO.php \
        app/config/database.config.php \
        app/config/server.config.php \
        app/config/env.config.php \
        app/helpers/logger.helper.php \
        app/helpers/validator.helper.php \
        app/utils/crypto.util.php \
        app/utils/response.util.php \
        app/routes/index.routes.php \
        app/routes/user.routes.php \
        app/routes/auth.routes.php
    do
        cria_arquivo "$file"
    done
}

# ================================
# Criar estrutura base
# ================================
create_base_folders() {
    for dir in controller model view service repository middleware entity dto \
               config helpers utils routes
    do
        mkdir -p "$BACKEND_DIR/app/$dir"
    done

    mkdir -p "$BACKEND_DIR/public" "$BACKEND_DIR/tests" \
             "$BACKEND_DIR/scripts" "$BACKEND_DIR/docs"

    touch "$BACKEND_DIR/.gitignore"
    touch "$BACKEND_DIR/.env"
}

# ==============
# MENUS
# ==============
main_menu() {
    echo ""
    echo "========= MENU PRINCIPAL ========="
    echo "1 | Estrutura MVC"
    echo "2 | VANILLA | HTML | CSS | JS | Basic"
    echo "=================================="
    read -p "Escolha: " OPT_MAIN
}

sub_menu_mvc() {
    echo "========= MVC ========="
    echo "1 | Backend JS + Angular"
    echo "2 | Backend TS + Angular"
    echo "3 | Backend TS + React"
    echo "4 | Backend JS + React"
    echo "5 | Backend JS + React"
    echo "6 | Backend JS Modulos Preencher + React"
    read -p "Escolha: " OPT_MVC
}

sub_menu_vanila() {
    echo "========= VANILLA ========="
    echo "1 | PHP| Basic | Login | HomePage | Register HTML Basic"
    echo "2 | JS | Basic | Login | HomePage | Register HTML Basic"
    echo "3 | TS | Basic | Login | HomePage | Register HTML Basic"
    read -p "Escolha: " OPT_VAN
}

# ======================================
# JSON e Database Exemplo
# ======================================
create_data_json_for_test() {
cat <<EOF > "$JSON_DIR/test.json"
{
    "Name":"Name 1",
    "Age":19,
    "Country": "BR",
    "State": "SP",
    "City" :"City1"
}
EOF
}

create_database_for_teste(){
cat <<EOF > "$DATABASE_DIR/test.sql"
-- Database For testes
CREATE DATABASE teste;
USE teste;
CREATE TABLE teste1(
    id INT AUTO_INCREMENT PRIMARY KEY NOT NULL,
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL,
    city VARCHAR(100) NOT NULL,
    country VARCHAR(100) NOT NULL
);
EOF
}

# ================================
# .env
# ================================

create_env(){
    cat <<eof > "$BACKEND_DIR/.env"
    PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASS=root
DB_NAME=app_db
JWT_SECRET=changeme
eof
}

create_env_docker_archives(){
    cat <<eof > "$BASE_DIR/.env.docker"
    MYSQL_ROOT_PASSWORD=root
MYSQL_DATABASE=app_db
MYSQL_USER=root
MYSQL_PASSWORD=root
APP_PORT=3000
eof
}

create_docker_files(){
    cat <<eof > "$BASE_DIR/docker-compose.yml"
version: "3.9"
services:
  backend:
    build: ./Backend
    container_name: backend_app
    ports:
      - "${APP_PORT}:3000"
    env_file:
      - .env.docker
    depends_on:
      - db
    volumes:
      - ./Backend:/app
    command: npm run dev
  db:
    image: mysql:8.0
    container_name: mysql_db
    restart: always
    env_file:
      - .env.docker
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql
volumes:
  mysql_data:

eof
}

# ================================
# DEPENDÊNCIAS
# ================================
install_dependencies_1(){
  cd "$BACKEND_DIR" || exit
  npm init -y
  npm install express typeorm reflect-metadata mysql2 bcrypt jsonwebtoken dotenv cors passport passport-jwt class-validator class-transformer
  npm install -D typescript ts-node @types/node @types/express @types/jsonwebtoken @types/bcrypt @types/cors ts-node-dev
}

install_dependencies_2(){
  cd "$BACKEND_DIR" || exit
  npm init -y
  npm install @prisma/client
  npx prisma init
  npm install prisma reflect-metadata mysql2 bcrypt jsonwebtoken dotenv cors passport passport-jwt class-validator class-transformer
  npm install -D typescript ts-node @types/node @types/express @types/jsonwebtoken @types/bcrypt @types/cors ts-node-dev
}

# ================================
# React Native (Expo)
# ================================

criar_react_vite_ts(){
    echo "🅰 Criando React (Vite + TS)..."

    cd "$FRONTEND_DIR" || exit 1

    PROJECT_REACT="frontend-react-ts"

    npm create vite@latest "$PROJECT_REACT" -- --template react-ts

    cd "$PROJECT_REACT" || exit 1

    npm install

    echo "✅ React TS criado em: $FRONTEND_DIR/$PROJECT_REACT"
}

criar_react_native_vite_js(){
    echo "🅰 Criando React (Vite + TS)..."

    cd "$FRONTEND_DIR" || exit 1

    PROJECT_REACT="frontend-react-ts"

    npm create vite@latest "$PROJECT_REACT" -- --template react-ts

    cd "$PROJECT_REACT" || exit 1

    npm install

    echo "✅ React TS criado em: $FRONTEND_DIR/$PROJECT_REACT"
}


cria_angular() {
    echo "🅰 Criando projeto Angular..."

    npm install -g @angular/cli

    cd "$FRONTEND_DIR"

    ng new Frontend_Angular --defaults --skip-git

    echo "✨ Angular criado em: $BASE_DIR/Frontend_Angular"
}


create_doc(){
    touch "$BACKEND_DIR/docs/README.md"
    touch "$BACKEND_DIR/docs/Version.md"
    touch "$BACKEND_DIR/docs/LICENSE.md"
    touch "$BACKEND_DIR/docs/CONTRIBUTING.md"
    touch "$BACKEND_DIR/docs/routes.md"
}

frontend_vanilla(){
    mkdir -p "$FRONTEND_DIR/assets/css"
    mkdir -p "$FRONTEND_DIR/assets/js"
    cat <<EOF >>"$FRONTEND_DIR/index.html"
    <!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Homepage</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
    <script src=""></script>
</head>
<body>
    <nav>
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </nav>
    <main>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </main>
    <footer>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >>"$FRONTEND_DIR/login.html"
    <!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login | Page</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
    <script src=""></script>
</head>
<body>
    <nav>
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </nav>
    <main>
    <input type="text" placeholder="usuario">
    <input type="password" placeholder="password">
    </main>
    <footer>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >>"$FRONTEND_DIR/register.html"
    <!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Register | Page</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
    <script src=""></script>
</head>
<body>
    <nav>
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </nav>
    <main>
    <input type="text" placeholder="usuario">
    <input type="password" placeholder="password">
    <input type="text">
    <input type="text">
    <input type="text">
    <input type="text">
    </main>
    <footer>
        <div></div>
        <div></div>
        <div></div>
    </footer>
</body>
</html>
EOF
cat <<EOF >"$FRONTEND_DIR/about.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About | Page</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
</head>
<body>
    <nav>
        <ul>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
        </ul>
    </nav>

    <main>
        <div>Info</div>
        <div>Info</div>
        <div>Info</div>
        <div>Info</div>
        <div>Info</div>
        <div>Info</div>
        <div>Info</div>
    </main>

    <footer>
        <div>Info</div>
        <div>Info</div>
        <div>Info</div>
    </footer>
</body>
</html>
EOF
cat <<EOF >"$FRONTEND_DIR/Products.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About | Page</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
</head>
<body>
    <nav>
        <ul>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
        </ul>
    </nav>

    <main>
        <!-- products.html -->
<nav></nav>

<main>
    <section id="products-list"Info></section>

    <section id="product-form">Info</section>

    <section id="product-details">Info</section>
</main>
    </main>

    <footer>
        <div>Info</div>
        <div>Info</div>
        <div>Info</div>
    </footer>
</body>
</html>
EOF
cat <<EOF >"$FRONTEND_DIR/Contact.html"
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About | Page</title>
    <link rel="stylesheet" href="../css/style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
</head>
<body>
    <nav>
        <ul>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
            <li>Info</li>
        </ul>
    </nav>

    <main>
    <nav></nav>

<main>
    <section id="contact-form"></section>
    <section id="support-info"></section>
</main>
    </main>

    <footer>
        <div>Info</div>
        <div>Info</div>
        <div>Info</div>
    </footer>
</body>
</html>
EOF
 cat <<EOF >>"$FRONTEND_DIR/assets/functions.js"
 //Functions for bootoms
function teste1(){}
function teste2(){}
function teste3(){}
function teste4(){}
function teste5(){}
EOF
 cat <<EOF >> "$BACKEND_DIR/server.js"
 // Import lib
const express = require('express')

// create instance express
const app = express()

// lib for json
app.use(express.json())

// Server Port
const PORT = 3000

//Routes for teste
app.get('/home',(req,res)=>{
    res.send('Homepage');
})
app.post('/home/login',(req,res)=>{
    res.send('Login Page');
})
app.get('/home/register',(req,res)=>{
    res.send('Register Page');
})
app.get('/home/contact',(req,res)=>{
    res.send('Contact Page');
})
app.get('/home/About',(req,res)=>{
    res.send('About Page');
})

// Function test (For register in JSON)
app.post('/usuarios',(req,res)=>{
   const novoUsuario = req.body;
   console.log("New User Register",novoUsuario)
   res.status(201).json({
    mensagem: "User Register Sucess",
    usuario: novoUsuario
   })
})
EOF
}

teste_ts_sistema_soma(){
    cat <<EOF >>"$TESTS_DIR/tests/soma.test.ts"
    import { teste, verifica } from "../src/a";
import { diminuir } from "../src/a";
import { mult } from "../src/a";
import { div } from "../src/a";

test("subtrair números positivos", () => {
    expect(diminuir(10,3)).toBe(7);
});

test("subtrair números negativo", () => {
    expect(diminuir(-5,-3)).toBe(-2);
});

test("subtrair com zero", () => {
    expect(diminuir(7,0)).toBe(7);
    expect(diminuir(0,7)).toBe(-7);
});

test("Multiplcar Numeros positivos",()=>{
    expect(mult(4,5)).toBe(20);
});

test("Multiplcar Numeros Negativos",()=>{
    expect(mult(-4, 5)).toBe(-20);
    expect(mult(-4, -5)).toBe(20);
});

test("multiplicar por zero", () => {
        expect(mult(10, 0)).toBe(0);
        expect(mult(0, 10)).toBe(0);
});

    // === DIVISÃO ===
test("dividir números positivos", () => {
        expect(div(10, 2)).toBe(5);
});

test("dividir números negativos", () => {
        expect(div(-10, 2)).toBe(-5);
        expect(div(-10, -2)).toBe(5);
});

test("dividir zero por número não zero", () => {
        expect(div(0, 5)).toBe(0);
});

test("Verifica se o Numero e Par ou Impar", () => {
        expect(verifica(3, 3)).toBe(1);
});

test("divisão por zero deve lançar erro", () => {
        expect(() => div(10, 0)).toThrow("Divisão por zero não permitida");
        expect(() => div(-5, 0)).toThrow();
        expect(() => div(0, 0)).toThrow();
});
EOF
}


teste_ts_sistema_validarUsuario(){
    cat <<EOF >>"$TESTS_DIR/tests/validarUsuario.test.ts"
import { validarUsuario, Usuario } from "../src/x";

describe("Validação de usuário", () => {
    
    test("Usuário válido deve retornar true", () => {
        const usuario: Usuario = {
            nome: "Usuario Exemplo",
            idade: 25
        };
        expect(validarUsuario(usuario)).toBe(true);
    });

    test("Nome vazio deve retornar false", () => {
        const usuario: Usuario = {
            nome: "",
            idade: 25
        };
        expect(validarUsuario(usuario)).toBe(false);
    });

    test("Nome com apenas espaços deve retornar false", () => {
        const usuario: Usuario = {
            nome: "   ",
            idade: 25
        };
        expect(validarUsuario(usuario)).toBe(false);
    });

    test("Menor de idade (17 anos) deve retornar false", () => {
        const usuario: Usuario = {
            nome: "Menor",
            idade: 17
        };
        expect(validarUsuario(usuario)).toBe(false);
    });

    test("Usuário com nome válido mas idade negativa deve retornar false", () => {
        const usuario: Usuario = {
            nome: "IdadeNegativa",
            idade: -5
        };
        expect(validarUsuario(usuario)).toBe(false);
    });
});
EOF
}

teste_ts_sistema_validarSenha(){
    cat <<EOF >>"$TESTS_DIR/tests/validarUsuario.test.ts"
import { senhaForte } from "../src/senha";

describe("Validação de senha forte", () => {
    
    test("Senha válida (8+ caracteres e com número) deve retornar true", () => {
        expect(senhaForte("abc12345")).toBe(true);
        expect(senhaForte("senhaForte123")).toBe(true);
        expect(senhaForte("12345678")).toBe(true);
    });

    test("Senha com menos de 8 caracteres deve retornar false", () => {
        expect(senhaForte("abc123")).toBe(false);      // 6 caracteres
        expect(senhaForte("1234567")).toBe(false);     // 7 caracteres
        expect(senhaForte("curta")).toBe(false);       // 5 caracteres
    });

    test("Senha sem número deve retornar false", () => {
        expect(senhaForte("abcdefgh")).toBe(false);    // 8 letras, sem número
        expect(senhaForte("senhaForte")).toBe(false);  // letras, sem número
        expect(senhaForte("!@#$%¨&*")).toBe(false);    // símbolos, sem número
    });

    test("Casos extremos: string vazia e espaços", () => {
        expect(senhaForte("")).toBe(false);            // vazia
        expect(senhaForte("        ")).toBe(false);    // 8 espaços (não tem número)
        expect(senhaForte("a b c 1")).toBe(false);     // 7 caracteres (espaços contam)
    });
});
EOF
}

novo_arquivos_backend1(){
cat <<EOF > "$BACKEND_DIR/.env"
DB_HOST=
DB_PORT=
DB_USER=
DB_Password=
DB_DATABASE=
JWT_Secret=chave_aqui
EOF
}

novos_arquivos_backend2(){
cat <<EOF > "$BACKEND_DIR/app/config/database.js"
import mysql from "mysql2/promise";

import { DB_DATABASE } from "./env-config.js";
import { DB_PORT } from "./env-config.js";
import { DB_HOST } from "./env-config.js";
import { DB_USER } from "./env-config.js";
import { DB_Password } from "./env-config.js";

export const conn = mysql.createPool({
   host:DB_HOST,
   port: parseInt(DB_PORT|| '3306'),
   user: DB_USER,
   password: DB_Password,
   database:DB_DATABASE,
   waitForConnections:true,
   connectionLimit: seu_limite_aqui
})
EOF
cat <<EOF > "$BACKEND_DIR/app/config/env-config.js"
import dotenv from "dotenv";

dotenv.config();

export const {DB_HOST, DB_PORT, DB_USER, DB_Password, DB_DATABASE,JWT_Secret}= process.env;
EOF
}

novo_arquivos_backend3(){
cat <<EOF > "$BACKEND_DIR/app/controller/user-controller.js"
import { UserService } from "../services/user-services.js";
export class UserController{

    static async index(req,res){
         const usuarios = await UserService.exibirUsuarios();
         res.status(200).json(usuarios)
    }

    static async findID(res,req){
        const id = parseInt(req.params.id_usuario);
        const usuario = await UserService.exibirUsuario(id);
        res.status(200).json(usuario)
    }

    static async register(req,res){
        const {nome, idade, telefone, email,senha} = req.body;
        const novoUsuario = await UserService.RegistrarUsuario(nome,idade ,telefone ,email, senha)
        res.status(201).json(novoUsuario)
    }

  static async delete(req, res) {
    const id = parseInt(req.params.id);

    await UserService.delete(id)
    res.status(204).send("Usuario Não Encontrado | Favor Verificar!")
}

static async update(req, res) {
    const id = parseInt(req.params.id);
    const {nome,idade ,telefone ,email, senha} = req.body;
    const usuarioAtualizado = await UserService.update(id,nome,idade ,telefone ,email, senha)

    return res.status(200).json(usuarioAtualizado);
}

static async login(req,res){
    const {email,senha} = req.body
    const {token} = await UserService.login(email,senha)
    res.status(200).json({token})

}
}
EOF
}

novo_arquivo_backend4(){
cat <<EOF > "$BACKEND_DIR/app/middleware/error-handle.js"
export class AppError extends Error{
    constructor(message,statusCode){
     super(message)
     this.statusCode = statusCode
     this.isOperation = true
    }
}
EOF
cat <<EOF > "$BACKEND_DIR/app/middleware/Auth-middleware.js"
import jwt from 'jsonwebtoken'
import {AppError} from '../errors/error-handle.js'
import {JWT_Secret} from '../config/env-config.js'

export function authMiddleware(req,res,next){
   const authHeader = req.headers.authorization
   if(!authHeader){
    throw new AppError('Token Não Forncedido',401)
   }
   const [,token] = authHeader.split(' ')
   try{
     const decoded = jwt.verify(token,JWT_Secret)
     req.user = decoded
     next()
   }catch{
      throw new AppError('Token Expirado',401)
   }
}
EOF
cat <<EOF > "$BACKEND_DIR/app/middleware/error-middleware.js"
export function erroMiddleware(err,req,res,next){
   const status = err.statusCode || 500
   const isOperation = err.isOperation || false
   res.status(status).json({mensagem: isOperation ? err.message : "Erro Inesperado. Teste Novamente mais Tarde"})
}
EOF
}

novo_arquivos_backend5(){
cat <<EOF > "$BACKEND_DIR/app/service/user-repository.js"
// Backend/app/services/user-services.js
import { conn } from "../config/database.js";
import bcrypt from "bcrypt";
import jwt from "jsonwebtoken";
import { JWT_Secret } from "../config/env-config.js";

export class UserService {
    
    // ================================
    // LISTAR TODOS OS USUÁRIOS
    // ================================
    static async exibirUsuarios() {
        const [rows] = await conn.query("SELECT * FROM sua_tabela_aqui");
        return rows;
    }

    // ================================
    // BUSCAR USUÁRIO POR ID
    // ================================
    static async exibirUsuario(id) {
        const [rows] = await conn.query("SELECT * FROM sua_tabela_aqui WHERE id = ?", [id]);
        return rows[0];
    }

    // ================================
    // BUSCAR USUÁRIO POR EMAIL
    // ================================
    static async buscarPorEmail(email) {
        const [rows] = await conn.query("SELECT * FROM sua_tabela_aqui WHERE email = ?", [email]);
        return rows[0];
    }

    // ================================
    // REGISTRAR NOVO USUÁRIO
    // ================================
    static async RegistrarUsuario(nome, idade, telefone, email, senha) {
        // Verifica se email já existe
        const usuarioExistente = await this.buscarPorEmail(email);
        if (usuarioExistente) {
            throw new Error("E-mail já cadastrado");
        }

        // Criptografa a senha
        const saltRounds = 10;
        const senhaHash = await bcrypt.hash(senha, saltRounds);

        // Insere no banco
        const [result] = await conn.query(
            "INSERT INTO sua_tabela_aqui (nome, idade, telefone, email, senha) VALUES (?, ?, ?, ?, ?)",
            [nome, idade, telefone, email, senhaHash]
        );

        // Retorna o usuário criado
        return {
            id: result.insertId,
            nome,
            idade,
            telefone,
            email
        };
    }

    // ================================
    // DELETAR USUÁRIO POR ID
    // ================================
    static async delete(id) {
        const [result] = await conn.query("DELETE FROM sua_tabela_aqui WHERE id = ?", [id]);
        
        if (result.affectedRows === 0) {
            throw new Error("Usuário não encontrado");
        }
        
        return true;
    }

    // ================================
    // ATUALIZAR USUÁRIO
    // ================================
    static async update(id, nome, idade, telefone, email, senha) {
        // Verifica se usuário existe
        const usuario = await this.exibirUsuario(id);
        if (!usuario) {
            throw new Error("Usuário não encontrado");
        }

        // Prepara os dados para atualização
        let senhaHash = usuario.senha;
        if (senha) {
            const saltRounds = 10;
            senhaHash = await bcrypt.hash(senha, saltRounds);
        }

        // Atualiza no banco
        const [result] = await conn.query(
            "UPDATE sua_tabela_aqui SET nome = ?, idade = ?, telefone = ?, email = ?, senha = ? WHERE id = ?",
            [nome || usuario.nome, idade || usuario.idade, telefone || usuario.telefone, email || usuario.email, senhaHash, id]
        );

        // Retorna o usuário atualizado
        return {
            id,
            nome: nome || usuario.nome,
            idade: idade || usuario.idade,
            telefone: telefone || usuario.telefone,
            email: email || usuario.email
        };
    }

    // ================================
    // LOGIN
    // ================================
    static async login(email, senha) {
        // Busca usuário pelo email
        const usuario = await this.buscarPorEmail(email);
        if (!usuario) {
            throw new Error("Email ou senha inválidos");
        }

        // Compara a senha com o hash
        const senhaValida = await bcrypt.compare(senha, usuario.senha);
        if (!senhaValida) {
            throw new Error("Email ou senha inválidos");
        }

        // Gera o token JWT
        const token = jwt.sign(
            { id: usuario.id, email: usuario.email },
            JWT_Secret,
            { expiresIn: "30m" }
        );

        return { token, usuario: { id: usuario.id, nome: usuario.nome, email: usuario.email } };
    }
}
EOF
}

novo_arquivos_backend6(){
cat <<EOF > "$BACKEND_DIR/app/model/use-model.js" 
 export class Usuario{
    constructor(id,nome,idade,telefone,email,senha){
    this.id = id;
    this.nome = nome;
    this.idade = idade;
    this.telefone = telefone;
    this.email = email;
    this.senha = senha;
    }
}
EOF  
cat <<EOF > "$BACKEND_DIR/app/model/product-model.js"
export class Produto {
    constructor(id, nome, descricao, preco, quantidade, categoria, createdAt, updatedAt) {
        this.id = id;
        this.nome = nome;
        this.descricao = descricao;
        this.preco = preco;
        this.quantidade = quantidade;
        this.categoria = categoria;
        this.createdAt = createdAt || new Date();
        this.updatedAt = updatedAt || new Date();
    }
}
EOF
cat <<EOF > "$BACKEND_DIR/app/model/order-model.js"
export class Pedido {
    constructor(id, usuarioId, status, total, itens, createdAt, updatedAt) {
        this.id = id;
        this.usuarioId = usuarioId;
        this.status = status; // 'pendente', 'pago', 'enviado', 'entregue', 'cancelado'
        this.total = total;
        this.itens = itens || []; // array de objetos {produtoId, quantidade, preco}
        this.createdAt = createdAt || new Date();
        this.updatedAt = updatedAt || new Date();
    }
    adicionarItem(produtoId, quantidade, preco) {
        this.itens.push({ produtoId, quantidade, preco });
        this.total += quantidade * preco;
    }
}
EOF
cat <<EOF > "$BACKEND_DIR/app/model/auth-model.js"
export class Auth {
    constructor(usuarioId, token, refreshToken, expiresAt, userAgent, ip) {
        this.usuarioId = usuarioId;
        this.token = token;
        this.refreshToken = refreshToken;
        this.expiresAt = expiresAt;
        this.userAgent = userAgent;
        this.ip = ip;
        this.createdAt = new Date();
    }

    isExpired() {
        return new Date() > new Date(this.expiresAt);
    }
    }
EOF
cat <<EOF > "$BACKEND_DIR/app/model/base-model.js"
export class BaseModel {
    constructor(id, createdAt, updatedAt) {
        this.id = id;
        this.createdAt = createdAt || new Date();
        this.updatedAt = updatedAt || new Date();
    }

    update() {
        this.updatedAt = new Date();
    }
}
EOF
cat <<EOF > "$BACKEND_DIR/.gitignore"
# Ignora Nodules 
node_modules/
EOF
}

# ======================================
# CHAMADA DO MENU
# ======================================
main_menu

create_data_json_for_test
create_database_for_teste

echo "Script pronto! 🚀"

case $OPT_MAIN in

  # ==================== MVC ====================
  1)
    sub_menu_mvc
    case $OPT_MVC in
      1)
    create_base_folders
    backend_js
    cria_angular
    create_doc
    create_env
      ;;
      2)
    create_base_folders
    backend_ts
    cria_angular
    create_doc
    create_env
    install_dependencies_1
    teste_ts_sistema_soma
    teste_ts_sistema_validarSenha
    teste_ts_sistema_validarUsuario
      ;;
      3)
    create_base_folders
    backend_ts
    create_doc
    criar_react_vite_ts
    install_dependencies_1
    create_env
    teste_ts_sistema_soma
    teste_ts_sistema_validarSenha
    teste_ts_sistema_validarUsuario
    ;;
    4)
    create_base_folders
    backend_js
    create_doc
    criar_react_native_vite_js
    create_env
     ;;

     5) create_base_folders
     backend_ts
     install_dependencies_1
     create_doc
     criar_react_vite_ts
     create_env_docker_archives
     create_env
     create_data_json_for_test
     create_docker_files
     teste_ts_sistema_soma
    teste_ts_sistema_validarSenha
    teste_ts_sistema_validarUsuario
     ;;
     6)create_base_folders
       novo_arquivos_backend1
       novos_arquivos_backend2
       novo_arquivos_backend3
       novo_arquivo_backend4
       novo_arquivos_backend5
       novo_arquivos_backend6
       create_doc
       criar_react_vite_ts
       create_env_docker_archives
       create_data_json_for_test
       create_docker_files
       teste_ts_sistema_soma
       teste_ts_sistema_validarSenha
       teste_ts_sistema_validarUsuario
       install_dependencies_1
    ;;
      *)
        echo "Opção inválida no menu MVC"
      ;;
    esac
  ;;

  # ========== VANILLA ==========
  2)
    sub_menu_vanila
    case $OPT_VAN in
      1) backend_php; frontend_vanilla; create_doc ;;
      2) backend_js; frontend_vanilla; create_doc ;;
      3) backend_ts; frontend_vanilla; create_doc ;;
      *)
        echo "Opção inválida"
      ;;
    esac
  ;;
esac
```
