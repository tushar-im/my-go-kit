# my-go-kit 🧰

> Serverless Go boilerplate for building REST APIs on AWS — optimized for the AWS Free Tier.

---

## ✨ Features

- ⚡️ **Go + Fiber** web framework
- 🗃 **PostgreSQL** via **Aurora Serverless v2 + Data API (DSQL)**
- 🔐 **Stateless JWT auth**
- 🔑 **TOTP support** using [`pquerna/otp`](https://github.com/pquerna/otp) + **Redis-backed challenge store**
- 📬 **Email integration** via AWS SES
- ☁️ **S3 file uploads** (presigned URLs)
- 🛠 **GORM** ORM (with PGX driver)
- 🚀 **Hot Reload** with [AIR](https://github.com/air-verse/air)
- 🛡 Fully serverless deploy using **AWS Lambda** + **API Gateway**
- 🧱 Infrastructure-as-Code with **Terraform**
- 🔐 Secure IAM-based access to DB, S3, SES, and Redis (optional ElastiCache)

---

## 🏗️ Infrastructure Overview

All infrastructure is designed to be within **AWS Free Tier limits**:

| Service            | Purpose                            |
|--------------------|-------------------------------------|
| AWS Lambda         | Runs Go backend (stateless)        |
| Aurora DSQL        | Postgres via HTTP, no idle cost    |
| Amazon SES         | Send magic links, TOTP codes       |
| Amazon S3          | File uploads (avatars, wishlist)   |
| API Gateway        | Public HTTP access to Lambda       |
| IAM                | Secure permissions for each module |
| Amazon ElastiCache | Redis store for TOTP/session use   |

---

## 📁 Project Structure

```bash
my-go-kit/
├── cmd/main.go                # Lambda/Fiber entrypoint
├── internal/
│   ├── users/                 # Domain module for users
│   │   ├── apis.go            # Handlers for user routes
│   │   ├── models.go          # GORM models
│   │   └── service.go         # Domain-specific logic (e.g. check if email exists)
│   ├── auth/                  # JWT + TOTP logic
│   ├── db/                    # Aurora DSQL + SQL helpers
│   ├── email/                 # SES integration
├── pkg/                       # Shared helpers/utilities
├── .air.toml                  # AIR config for hot reload
├── Makefile                   # Dev + build automation
├── terraform/                 # Modular AWS infra
│   ├── main.tf                # Root infra composition
│   └── modules/               # Lambda, RDS, SES, S3, Redis, etc.
├── go.mod / go.sum            # Go dependencies
└── README.md
```

---

## 🧪 Tech Stack

| Layer         | Stack                           |
|---------------|----------------------------------|
| Language      | Go                              |
| Framework     | Fiber                           |
| ORM           | GORM (with PGX)                 |
| Auth          | JWT (stateless) + TOTP + Redis  |
| Email         | SES                             |
| DB            | Aurora Serverless v2 (DSQL)     |
| Infra         | Terraform                       |
| Deploy        | Lambda + API Gateway            |
| Storage       | S3                              |
| Monitoring    | CloudWatch (basic)              |

---

## 🧭 Getting Started

Coming soon — Terraform init, Lambda deploy, and API bootstrap steps.

---

## 📜 License

MIT

---

