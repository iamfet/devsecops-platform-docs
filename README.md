# End-to-End DevSecOps Platform

**Automated DevSecOps ecosystem** with complete pipeline from code commit to production deployment on Amazon EKS.

## 🎯 What This Is

Three integrated repositories demonstrating complete automated DevSecOps pipeline:

```
🏗️ Infrastructure → 📱 Applications → 🔄 GitOps → 🛡️ Security
```

**Why It Matters**: End-to-end automation - security embedded, zero-trust architecture, production-ready.

## 🏗️ Architecture Overview

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│🏗️ Infrastructure│───▶│ 📱 Application  │───▶│ 🔄 GitOps       │
│ EKS + Security  │    │ Build + Scan    │    │ Deploy + Sync   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                        🛡️ DefectDojo Security Hub
```

**How They Connect**: Repository dispatch triggers, automated sync, integrated pipeline.

## 📁 The Three Repositories

### **1. 🏗️ Infrastructure Repository** 
**[sec-eks-infra-automation](./sec-eks-infra-automation/)**

**Purpose**: Provisions and manages the entire AWS EKS infrastructure using Terraform

**Key Components**:
- **EKS Cluster**: Managed Kubernetes with fine-grained RBAC
- **Security Stack**: Vault, OPA Gatekeeper, Istio service mesh
- **Monitoring**: Prometheus, Grafana with custom dashboards
- **GitOps Engine**: ArgoCD for continuous deployment
- **AWS Integration**: Pod Identity, Load Balancer Controller, cert-manager

**Technologies**: Terraform, Helm, AWS EKS, AWS KMS, AWS Secrets Manager, HashiCorp Vault, Istio, OPA Gatekeeper, ArgoCD, Prometheus, Grafana, cert-manager, External Secrets Operator, GitHub Actions

### **2. 📱 Application Repository**
**[sec-online-boutique-appliation](./sec-online-boutique-appliation/)**

**Purpose**: Contains microservices source code with comprehensive security scanning

**Key Components**:
- **11 Microservices**: Go, Java, Python, Node.js, C# applications
- **Security Scanning**: SonarQube, Gitleaks, Snyk, Trivy integration
- **Container Security**: Multi-stage builds, distroless images
- **CI/CD Pipeline**: Automated testing, building, and security validation
- **DefectDojo Integration**: Vulnerability management and reporting

**Technologies**: Go, Java, Python, Node.js, C#, Docker, GitHub Actions, SonarQube, Gitleaks, Snyk, Trivy, DefectDojo, Multi-stage builds, Distroless images

### **3. 🔄 GitOps Repository**
**[sec-gitops-online-boutique](./sec-gitops-online-boutique/)**

**Purpose**: Manages Kubernetes deployments and configurations using GitOps principles

**Key Components**:
- **Kustomize Manifests**: Base configurations and environment overlays
- **Security Policies**: OPA Gatekeeper constraint templates
- **Cluster Resources**: Monitoring, networking, and security configurations
- **ArgoCD Applications**: Automated deployment definitions
- **DefectDojo Deployment**: Vulnerability management platform

**Technologies**: Kustomize, ArgoCD, Kubernetes, YAML, OPA Gatekeeper, Istio VirtualServices, Prometheus ServiceMonitors, Grafana Dashboards, External Secrets, DefectDojo Helm Charts

## 🔄 Automated Workflow

#### **Phase 1: Infrastructure Setup** 🏗️
```bash
# GitHub Actions triggered on PR of .tf file
PR → GitHub Actions → terraform apply
# Result: EKS + Vault + Istio + ArgoCD + Monitoring
```

#### **Phase 2: Application Development** 📱
```bash
# Developer workflow
git commit → CI/CD → Security Scans → Container Build → Repository Dispatch
# Result: Secure images + Vulnerability reports + GitOps trigger
```

#### **Phase 3: GitOps Deployment** 🔄
```bash
# Automated deployment
Manifest Update → ArgoCD Sync → Policy Validation → Live Deployment
# Result: Compliant, monitored applications
```

## 🔒 Security Features

**Multi-Layer Defense**:
- **Code**: SAST, secrets detection, dependency scanning
- **Infrastructure**: Pod Identity, KMS, VPC isolation, RBAC
- **Runtime**: OPA policies, Istio mTLS, network policies
- **Monitoring**: DefectDojo vulnerability management hub

**Zero-Trust**: No hardcoded secrets, mTLS everywhere, automated policy enforcement.

## 🚀 Quick Start

**Prerequisites**: AWS account, Terraform ≥1.5, kubectl, AWS CLI

**Deploy Order**:
1. **Infrastructure** → GitHub Actions triggered → Bootstraps entire platform (see [infrastructure repo](./sec-eks-infra-automation/))
2. **GitOps** → Deployed by infrastructure (see [gitops repo](./sec-gitops-online-boutique/))
3. **Applications** → Triggered on code push (see [application repo](./sec-online-boutique-appliation/))

**Access**: Port-forward ArgoCD (8080), Grafana (3000), DefectDojo (8000)

## 🛡️ Security Hub

**DefectDojo** aggregates all security findings:
- Infrastructure scans → Terraform, AWS config
- Application scans → SAST, secrets, dependencies, containers  
- Runtime issues → Policy violations, deployment risks

**Result**: Unified dashboard with risk prioritization, trend analysis, compliance reporting.

## 📊 Monitoring

**Full Stack Observability**:
- **Infrastructure**: Prometheus + Grafana (cluster, nodes, pods)
- **Applications**: ServiceMonitors (performance, health, SLIs)
- **Security**: DefectDojo + Istio (vulnerabilities, mTLS)
- **Network**: Jaeger (distributed tracing)

**Dashboards**: Platform overview, security posture, performance, deployments.

## 🔐 Compliance

**Defense-in-Depth**: Edge protection, network security, policy enforcement, secrets management, identity control, code security, container security, audit trails.

**Compliance Cycle**: Infrastructure defines → GitOps enforces → Applications comply → DefectDojo reports.

## 🔧 Customization

**Adding Services**: 
1. Application repo → Add code + CI/CD
2. GitOps repo → Create manifests + policies
3. Infrastructure repo → Update monitoring
4. Integration → Repository dispatch connects all

**Environments**: Dev (direct sync), Staging (manual promotion), Production (approval-based)

**Policies**: Infrastructure defines → GitOps enforces → Applications comply → DefectDojo monitors

## 📚 Next Steps

**Explore Each Repository**:
- 🏗️ **[Infrastructure](./sec-eks-infra-automation/)** → Complete setup guide, Terraform configs
- 📱 **[Application](./sec-online-boutique-appliation/)** → Microservices code, security scanning
- 🔄 **[GitOps](./sec-gitops-online-boutique/)** → Deployment manifests, policies

**Learn More**:
- [AWS EKS Best Practices](https://aws.github.io/aws-eks-best-practices/)
- [GitOps Principles](https://opengitops.dev/)
- [DevSecOps Best Practices](https://www.devsecops.org/)

---

## 🎯 Why This Matters

✅ **Security-by-Design** - Multi-layer security embedded throughout  
✅ **End-to-End Automation** - Complete pipeline from code to production  
✅ **Zero-Trust** - No implicit trust, verify everything  
✅ **Production-Ready** - Scalable, monitored, maintainable

**Built for DevSecOps education and enterprise adoption**

📄 **License**: MIT - see individual repository LICENSE files