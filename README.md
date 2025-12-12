# Infrastructure AWS - MLOps G0MG00

Cette infrastructure Terraform approvisionne les services s3, ecr, ecs et apprunner.

## Services créés

L'infrastructure crée les services suivants avec le suffixe `G0MG00` :

1. **S3 Bucket** (`s3-g0mg00`)
   - Bucket S3 pour le stockage
   - Versioning activé
   - Chiffrement AES256

2. **ECR Repository** (`ecr-g0mg00`)
   - Repository pour les images Docker
   - Scan automatique des images
   - Politique de lifecycle (garde les 10 dernières images)

3. **ECS Cluster** (`ecs-g0mg00`)
   - Cluster ECS pour l'orchestration de conteneurs
   - Container Insights activé
   - Rôles IAM pour l'exécution des tâches

4. **App Runner Service** (`apprunner-g0mg00`)
   - Service App Runner pour le déploiement d'applications
   - Connecté au repository ECR
   - Configuration CPU: 1024, Mémoire: 2048 MB
   - Health check configuré

## Structure des fichiers

```
terraform/
├── main.tf                 
├── variables.tf            
├── outputs.tf            
├── .gitignore             
├── README.md              
└── modules/
    ├── s3/                # S3
    │   ├── main.tf
    │   ├── variables.tf
    │   └── outputs.tf
    ├── ecr/               # ECR
    │   ├── main.tf
    │   ├── variables.tf
    │   └── outputs.tf
    ├── ecs/               # ECS
    │   ├── main.tf
    │   ├── variables.tf
    │   └── outputs.tf
    └── apprunner/         # AppRunner
        ├── main.tf
        ├── variables.tf
        └── outputs.tf
```