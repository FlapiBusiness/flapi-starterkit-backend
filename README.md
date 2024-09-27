# Flapi - StarterKit BackEnd

## 🛠 Tech Stack

- TypeScript (Language)
- Adonis (Framework)
- CI / CD (Github Actions)
- Docker / DockerCompose (Development-Local)
- Kubernetes (Development-remote, Staging and Production)
- Unit / Functional Tests (Japa)

<br /><br /><br /><br />

## 📚 Domains of different environments

- Production : https://test.crzcommon.com
- Staging : https://staging.test.crzcommon.com
- Development-Remote : https://dev.test.crzcommon.com

<br /><br /><br /><br />

## ⚙️ Setup Environment Development

1. Clone the project repository using the following commands :

```bash
git clone git@github.com:FlapiBusiness/MyRepo.git
```

2. Steps by Platform :

```bash
# Windows :
1. Requirements : Windows >= 10
2. Download and Install WSL2 : https://learn.microsoft.com/fr-fr/windows/wsl/install
3. Download and Install Docker Desktop : https://docs.docker.com/desktop/install/windows-install/

# macOS :
1. Requirements : macOS Intel x86_64 or macOS Apple Silicon arm64
2. Requirements (2) : macOS 11.0 (Big Sur)
2. Download and Install Docker Desktop : https://docs.docker.com/desktop/install/mac-install/

# Linux (Ubuntu / Debian) :
1. Requirements : Ubuntu >= 20.04 or Debian >= 10
2. Download and Install Docker (Ubuntu) : https://docs.docker.com/engine/install/ubuntu/
3. Download and Install Docker (Debian) : https://docs.docker.com/engine/install/debian/
```

<br /><br /><br /><br />

## 🔄 Cycle Development

1. Open Docker Desktop
2. Run command :

```bash
   # Start the development server on http://localhost:3555 (AdonisJS)
   # Start the development server on http://localhost:7450 (PhpMyAdmin)
   # Start MariaDB port is : 3308
   npm install # just for the idea
   npm run dev:docker
```

<br /><br /><br /><br />

## 🔄 Unit / Functional Tests

1. Run command :

```bash
# Environment : Development
npm run test:develop

# Environment : Staging / Production
npm run test:staging-prod
```

<br /><br /><br /><br />

## 🚀 Production

### ⚙️➡️ Automatic Distribution Process (CI / CD)

#### Si c'est un nouveau projet suivez les instructions :

1. Ajoutées les SECRETS_GITHUB pour :
   - DOCKER_HUB_USERNAME
   - DOCKER_HUB_ACCESS_TOKEN
   - KUBECONFIG
   - PAT (crée un nouveau token si besoin sur le site de github puis dans le menu du "Profil" puis -> "Settings" -> "Developper Settings' -> 'Personnal Access Tokens' -> Tokens (classic))
