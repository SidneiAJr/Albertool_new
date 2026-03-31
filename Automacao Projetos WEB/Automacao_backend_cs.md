# 🚀 C# | Gerador de Projetos .NET | Projeto Open Source
**Foco:** Backend (C#)  
**Criado no Brasil 🇧🇷 para o mundo.**

Bem-vindo à documentação do **C# | Gerador de Projetos .NET**, uma ferramenta CLI para criação rápida de projetos .NET com estrutura profissional, seguindo o padrão MVC e boas práticas de mercado.

---

## 📌 Sobre a Ferramenta

A CLI foi desenvolvida para eliminar o trabalho repetitivo de criar pastas, arquivos e configurações iniciais em projetos C#/.NET. Com poucos comandos, você tem uma estrutura completa e pronta para desenvolvimento.

- ✔ **Simples** — Execute o script e informe o nome do projeto
- ✔ **Modular** — Escolha entre API, MVC ou Console
- ✔ **Rápido** — Estrutura pronta em segundos
- ✔ **Automático** — Gera arquivos de configuração, dependências e testes

---

## 📦 Requisitos

- ✅ [.NET SDK 8.0](https://dotnet.microsoft.com/download) instalado
- ✅ Git (opcional, para versionamento)
- ✅ Bash (Linux/Mac) ou Git Bash (Windows)

---

## 🧪 Dados de Teste

- ✔ Exemplo de teste unitário com xUnit
- ✔ Mock com Moq
- ✔ Configuração pronta para rodar testes

---

## 🙏 Agradecimento

Obrigado por utilizar esta ferramenta!  
Ela é simples, funcional e focada em produtividade.  
Se possível, aceito um café ☕ como forma de apoio — agradeço demais!

---

## 📚 Como Usar

1. Crie uma pasta no seu computador
2. Dentro dela, crie um arquivo com o script (ex: `setup.sh`)
3. Cole o conteúdo do script disponível no repositório
4. Salve o arquivo e execute com botão direto do Mouse gitbash.

## Script:
```bash
#!/bin/bash

echo "======================================"
echo "C# | Gerador de Projetos .NET"
echo "======================================"

read -p "Digite o nome do projeto: " PROJECT_NAME

# Diretórios base
BASE_DIR="$PROJECT_NAME"
BACKEND_DIR="$BASE_DIR/Backend"
FRONTEND_DIR="$BASE_DIR/Frontend"
JSON_DIR="$BASE_DIR/Json_Teste"
TESTS_DIR="$BASE_DIR/Tests"

mkdir -p "$BACKEND_DIR" "$FRONTEND_DIR" "$JSON_DIR" "$TESTS_DIR"

echo "📁 Projeto criado em: $BASE_DIR"

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
# Backend C#
# ===============================
backend_csharp(){
   for file in \
        app/controller/HomeController.cs \
        app/controller/UserController.cs \
        app/controller/AuthController.cs \
        app/model/UserModel.cs \
        app/model/ProductModel.cs \
        app/model/AuthModel.cs \
        app/service/UserService.cs \
        app/service/AuthService.cs \
        app/service/ProductService.cs \
        app/repository/UserRepository.cs \
        app/repository/ProductRepository.cs \
        app/middleware/auth.middleware.cs \
        app/middleware/error.middleware.cs \
        app/entity/UserEntity.cs \
        app/entity/ProductEntity.cs \
        app/dto/UserDTO.cs \
        app/dto/AuthDTO.cs \
        app/config/database.config.cs \
        app/config/server.config.cs \
        app/config/env.config.cs \
        app/helpers/logger.helper.cs \
        app/helpers/validator.helper.cs \
        app/utils/crypto.util.cs \
        app/utils/response.util.cs \
        app/routes/index.routes.cs \
        app/routes/user.routes.cs \
        app/routes/auth.routes.cs
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

# ================================
# Frontend React
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

# ================================
# Documentação
# ================================
create_doc(){
    touch "$BACKEND_DIR/docs/README.md"
    touch "$BACKEND_DIR/docs/Version.md"
    touch "$BACKEND_DIR/docs/LICENSE.md"
    touch "$BACKEND_DIR/docs/CONTRIBUTING.md"
    touch "$BACKEND_DIR/docs/routes.md"
}

# ================================
# Arquivos C#
# ================================
criar_csproj(){
    cat <<EOF > "$BACKEND_DIR/${PROJECT_NAME}.csproj"
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net8.0</TargetFramework>
    <Nullable>enable</Nullable>
    <ImplicitUsings>enable</ImplicitUsings>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="8.0.0" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Tools" Version="8.0.0" />
    <PackageReference Include="Swashbuckle.AspNetCore" Version="6.5.0" />
    <PackageReference Include="BCrypt.Net-Next" Version="4.0.3" />
    <PackageReference Include="System.IdentityModel.Tokens.Jwt" Version="7.0.0" />
  </ItemGroup>
</Project>
EOF
}

criar_program(){
    cat <<EOF > "$BACKEND_DIR/Program.cs"
using Microsoft.EntityFrameworkCore;
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.IdentityModel.Tokens;
using System.Text;
using ${PROJECT_NAME}.Data;
using ${PROJECT_NAME}.Services;
using ${PROJECT_NAME}.Repositories;

var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddControllers();
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

// Database
builder.Services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));

// JWT
var key = Encoding.ASCII.GetBytes(builder.Configuration["Jwt:Key"]);
builder.Services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
})
.AddJwtBearer(options =>
{
    options.RequireHttpsMetadata = false;
    options.SaveToken = true;
    options.TokenValidationParameters = new TokenValidationParameters
    {
        ValidateIssuerSigningKey = true,
        IssuerSigningKey = new SymmetricSecurityKey(key),
        ValidateIssuer = false,
        ValidateAudience = false
    };
});

// Dependency Injection
builder.Services.AddScoped<IUserService, UserService>();
builder.Services.AddScoped<IUserRepository, UserRepository>();
builder.Services.AddScoped<IAuthService, AuthService>();

var app = builder.Build();

// Configure the HTTP request pipeline.
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseHttpsRedirection();
app.UseAuthentication();
app.UseAuthorization();
app.MapControllers();

app.Run();
EOF
}

criar_appsettings(){
    cat <<EOF > "$BACKEND_DIR/appsettings.json"
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=${PROJECT_NAME};User Id=sa;Password=your_password;TrustServerCertificate=true;"
  },
  "Jwt": {
    "Key": "CHAVE_SUPER_SECRETA_AQUI_COM_PELO_MENOS_32_CARACTERES",
    "Issuer": "${PROJECT_NAME}",
    "Audience": "${PROJECT_NAME}"
  }
}
EOF
}

criar_model_user(){
    cat <<EOF > "$BACKEND_DIR/app/model/UserModel.cs"
namespace ${PROJECT_NAME}.Models;

public class User
{
    public int Id { get; set; }
    public string Name { get; set; } = string.Empty;
    public string Email { get; set; } = string.Empty;
    public string PasswordHash { get; set; } = string.Empty;
    public DateTime CreatedAt { get; set; } = DateTime.UtcNow;
}
EOF
}

criar_teste_usuario(){
    # Garante que a pasta tests existe
    mkdir -p "$TESTS_DIR"
    
    cat <<EOF > "$TESTS_DIR/UserServiceTests.cs"
using Xunit;
using Moq;
using ${PROJECT_NAME}.Services;
using ${PROJECT_NAME}.Repositories;

namespace ${PROJECT_NAME}.Tests;

public class UserServiceTests
{
    [Fact]
    public async Task GetUserById_ReturnsUser()
    {
        // Arrange
        var mockRepo = new Mock<IUserRepository>();
        mockRepo.Setup(repo => repo.GetByIdAsync(1))
            .ReturnsAsync(new User { Id = 1, Name = "Teste" });

        var service = new UserService(mockRepo.Object);

        // Act
        var user = await service.GetUserByIdAsync(1);

        // Assert
        Assert.NotNull(user);
        Assert.Equal("Teste", user.Name);
    }
}
EOF
}

criar_solucao(){
    cd "$BASE_DIR" || exit
    
    # Cria arquivo .sln
    dotnet new sln -n "$PROJECT_NAME"
    
    # Adiciona o projeto backend
    dotnet sln add "Backend/${PROJECT_NAME}.csproj"
    
    # Cria projeto de testes se não existir
    if [ ! -d "Tests/${PROJECT_NAME}.Tests" ]; then
        dotnet new xunit -n "${PROJECT_NAME}.Tests" -o "Tests/${PROJECT_NAME}.Tests"
        dotnet sln add "Tests/${PROJECT_NAME}.Tests/${PROJECT_NAME}.Tests.csproj"
        dotnet add "Tests/${PROJECT_NAME}.Tests/${PROJECT_NAME}.Tests.csproj" reference "Backend/${PROJECT_NAME}.csproj"
    fi
}

# ================================
# MENU
# ================================
echo ""
echo "========= MENU ========="
echo "1 | Backend C# + React"
echo "2 | Backend C# (somente API)"
echo "3 | React (somente frontend)"
echo "0 | Sair"
echo "========================"
read -p "Escolha: " OPT_MAIN

case $OPT_MAIN in
  1)
    create_base_folders
    backend_csharp
    criar_csproj
    criar_program
    criar_appsettings
    criar_model_user
    criar_teste_usuario
    criar_solucao
    criar_react_vite_ts
    create_doc
    echo "✅ Projeto completo criado!"
    ;;
  2)
    create_base_folders
    backend_csharp
    criar_csproj
    criar_program
    criar_appsettings
    criar_model_user
    criar_teste_usuario
    criar_solucao
    create_doc
    echo "✅ Backend C# criado!"
    ;;
  3)
    criar_react_vite_ts
    echo "✅ Frontend React criado!"
    ;;
  0)
    exit 0
    ;;
  *)
    echo "Opção inválida!"
    ;;
esac
```
