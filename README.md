# End-to-End DevSecOps Platform

**Complete enterprise-grade DevSecOps ecosystem** demonstrating security-first development practices with automated infrastructure provisioning, comprehensive security scanning, and GitOps-driven deployment on Amazon EKS.

## 🎯 Overview

This platform integrates **three specialized repositories** to create a complete DevSecOps pipeline that embeds security at every stage of the software delivery lifecycle:

### **🔄 Integration Flow**
```
🏗️ Infrastructure → 📱 Application Development → 🔄 GitOps Deployment → 🛡️ Security Monitoring
```

**Core Philosophy**: Security-by-design with automated enforcement, continuous monitoring, and zero-trust architecture across all components.

### **🎯 Key Benefits**
- **Security-First**: Multi-layer security with automated scanning and policy enforcement
- **Full Automation**: End-to-end pipeline from code commit to production deployment
- **Enterprise-Ready**: Production-grade infrastructure with monitoring and compliance
- **GitOps-Driven**: Declarative, auditable deployments with automated rollbacks

## 🏗️ Platform Architecture

### **Three-Repository Integration Model**

```
                    🔄 DevSecOps Platform Integration
    ┌───────────────────────────────────────────────────────────────────┐
    │                                                                   │
    ▼                           ▼                           ▼         │
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐    │
│ 🏗️ Infrastructure│    │ 📱 Application  │    │ 🔄 GitOps       │    │
│                 │    │                 │    │                 │    │
│ • EKS Cluster   │◀───│ • 11 Services   │───▶│ • Kustomize     │    │
│ • Vault/Secrets │    │ • Security Scans│    │ • ArgoCD Apps   │    │
│ • Istio Mesh    │    │ • CI/CD Pipeline│    │ • OPA Policies  │    │
│ • Monitoring    │    │ • DefectDojo    │    │ • Configurations│    │
│ • ArgoCD        │    │ • Multi-Language│    │ • Deployments   │    │
└─────────────────┘    └─────────────────┘    └─────────────────┘    │
         │                       │                       │           │
         └───────────────────────┼───────────────────────┘           │
                                 │                                   │
                    🛡️ DefectDojo Security Hub ◀────────────────────┘
```

### **Integration Points**
- **🔗 Repository Dispatch**: Automated triggers between Application → GitOps
- **🔒 Shared Security**: Common policies, secrets, and monitoring across all repos
- **📊 Unified Observability**: Centralized metrics, logs, and vulnerability tracking
- **⚖️ Policy Enforcement**: Infrastructure-defined constraints enforced at runtime

## 📁 Repository Breakdown

### **🏗️ Infrastructure Foundation**
**Repository**: [sec-eks-infra-automation](./sec-eks-infra-automation/)

**Role**: Provisions secure, production-ready AWS EKS infrastructure

| Component | Technology | Purpose |
|-----------|------------|---------|
| **EKS Cluster** | Terraform + AWS EKS | Managed Kubernetes with RBAC |
| **Security Layer** | Vault + OPA + Istio | Secrets, policies, service mesh |
| **Monitoring Stack** | Prometheus + Grafana | Metrics and visualization |
| **GitOps Engine** | ArgoCD | Continuous deployment |
| **AWS Services** | Pod Identity + KMS + ALB | Native AWS integration |

**Key Features**: Zero-trust networking, automated certificate management, policy-as-code enforcement

---

### **📱 Application Development**
**Repository**: [sec-online-boutique-appliation](./sec-online-boutique-appliation/)

**Role**: Multi-language microservices with embedded security scanning

| Service Type | Languages | Security Tools |
|--------------|-----------|----------------|
| **Frontend** | Go | SonarQube, golangci-lint |
| **Backend Services** | Go, Java, Python, Node.js, C# | Gitleaks, Snyk, Trivy |
| **Data Layer** | Redis | Container scanning |
| **CI/CD Pipeline** | GitHub Actions | DefectDojo integration |

**Security Features**: SAST, dependency scanning, secrets detection, container hardening

---

### **🔄 GitOps Deployment**
**Repository**: [sec-gitops-online-boutique](./sec-gitops-online-boutique/)

**Role**: Declarative deployments with policy enforcement

| Component | Technology | Function |
|-----------|------------|----------|
| **Base Manifests** | Kustomize | Service definitions |
| **Environment Overlays** | Kustomize | Dev/staging/prod configs |
| **Security Policies** | OPA Gatekeeper | Runtime constraints |
| **Networking** | Istio VirtualServices | Traffic management |
| **Monitoring** | ServiceMonitors | Observability configs |

**Key Features**: Automated image updates, policy validation, audit trails

### **Cross-Repository Technology Stack**

| Layer | Infrastructure Repo | Application Repo | GitOps Repo |
|-------|-------------------|------------------|-------------|
| **🏗️ Infrastructure** | Terraform, AWS EKS, VPC | - | Kustomize, YAML |
| **🔒 Security** | Vault, OPA, Istio, KMS | SonarQube, Gitleaks, Snyk, Trivy | OPA Policies, DefectDojo |
| **📊 Monitoring** | Prometheus, Grafana, Jaeger | - | ServiceMonitors, Dashboards |
| **🚀 Deployment** | ArgoCD, Helm Charts | Docker, Multi-stage builds | ArgoCD Apps, Kustomize |
| **🔄 Automation** | GitHub Actions, Terraform | GitHub Actions, Repository Dispatch | GitHub Actions, Auto-sync |

## 🔄 End-to-End Workflow

### **Complete Integration Pipeline**

```
┌─ 🏗️ INFRASTRUCTURE ─┐    ┌─ 📱 APPLICATION ─┐    ┌─ 🔄 GITOPS ─┐    ┌─ 🛡️ SECURITY ─┐
│                      │    │                  │    │             │    │               │
│ 1. Terraform Apply  │───▶│ 4. Code Commit   │───▶│ 7. Manifest │───▶│ 10. Policy    │
│ 2. EKS Cluster      │    │ 5. Security Scan │    │    Update   │    │     Validation│
│ 3. ArgoCD Bootstrap │    │ 6. Image Build   │    │ 8. ArgoCD   │    │ 11. DefectDojo│
│                      │    │                  │    │    Sync     │    │     Reporting │
└──────────────────────┘    └──────────────────┘    └─────────────┘    └───────────────┘
         │                           │                       │                    │
         └───────────────────────────┼───────────────────────┼────────────────────┘
                                     │                       │
                            Repository Dispatch      Continuous Monitoring
```

### **Deployment Phases**

#### **Phase 1: Infrastructure Setup** 🏗️
```bash
# Deploy secure EKS foundation
terraform apply
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

### **Integration Triggers**

| Trigger | Source | Target | Action |
|---------|--------|--------|---------|
| **Infrastructure Ready** | Terraform | ArgoCD | Deploy GitOps applications |
| **Code Commit** | Application | CI/CD | Run security scans |
| **Image Built** | Application | GitOps | Update deployment manifests |
| **Manifest Changed** | GitOps | ArgoCD | Sync to cluster |
| **Policy Violation** | OPA | DefectDojo | Security alert |

## 🔒 Security Integration

### **Multi-Layer Security Model**

```
🛡️ DEFENSE IN DEPTH ACROSS REPOSITORIES

┌─ CODE SECURITY ─┐  ┌─ INFRASTRUCTURE ─┐  ┌─ RUNTIME SECURITY ─┐
│ • SAST Scanning │  │ • Pod Identity    │  │ • OPA Policies     │
│ • Secrets Detection│ │ • KMS Encryption │  │ • Istio mTLS      │
│ • Dependency Scan│  │ • VPC Isolation   │  │ • Network Policies │
│ • Container Scan │  │ • RBAC Controls   │  │ • Admission Control│
└─────────────────┘  └─────────────────┘  └──────────────────┘
        │                     │                      │
        └─────────────────────┼──────────────────────┘
                              │
                    🎯 DefectDojo Security Hub
                   (Centralized Vulnerability Management)
```

### **Security Automation Flow**

| Stage | Repository | Security Controls | Integration |
|-------|------------|-------------------|-------------|
| **Development** | Application | SonarQube, Gitleaks, Snyk | → DefectDojo |
| **Build** | Application | Trivy, Multi-stage builds | → Secure images |
| **Deploy** | GitOps | OPA validation, Istio policies | ← Infrastructure policies |
| **Runtime** | Infrastructure | Monitoring, audit logs | → Centralized logging |

### **Zero-Trust Implementation**

- **🔐 No Hardcoded Secrets**: Vault + External Secrets across all repos
- **🌐 mTLS Everywhere**: Istio service mesh for all communications  
- **⚖️ Policy Enforcement**: OPA Gatekeeper validates every deployment
- **🔍 Continuous Scanning**: Automated vulnerability detection and reporting
- **📊 Unified Monitoring**: End-to-end observability and security metrics

## 🚀 Quick Start Guide

### **Prerequisites Checklist**
- ✅ AWS Account with EKS permissions
- ✅ GitHub repositories forked/cloned  
- ✅ Tools: Terraform ≥1.5, kubectl, AWS CLI
- ✅ Optional: Route53 domain for SSL certificates

### **Step-by-Step Deployment**

#### **Step 1: Infrastructure Foundation** 🏗️
```bash
# Clone and configure infrastructure
git clone <infrastructure-repo>
cd sec-eks-infra-automation

# Configure variables
cp terraform.tfvars.example terraform.tfvars
# Edit: user_for_admin_role, user_for_dev_role

# Deploy infrastructure
terraform init
terraform apply
```

#### **Step 2: Verify GitOps Setup** 🔄
```bash
# Configure kubectl
aws eks update-kubeconfig --region us-east-1 --name <cluster-name>

# Check ArgoCD applications
kubectl get applications -n argocd
kubectl get pods -n argocd
```

#### **Step 3: Access Platform Services** 🌐
```bash
# ArgoCD UI (GitOps dashboard)
kubectl port-forward svc/argocd-server -n argocd 8080:443
# → https://localhost:8080

# Grafana (Monitoring dashboard)  
kubectl port-forward svc/kube-prometheus-stack-grafana -n monitoring 3000:80
# → http://localhost:3000

# DefectDojo (Security dashboard)
kubectl port-forward svc/defectdojo -n defectdojo 8000:80
# → http://localhost:8000
```

### **Verification Commands**
```bash
# Platform health check
kubectl get nodes
kubectl get pods --all-namespaces | grep -E "argocd|monitoring|vault|istio"

# Security validation
kubectl get constrainttemplates
kubectl get certificates --all-namespaces
```

## 🛡️ DefectDojo Security Hub

### **Centralized Vulnerability Management**

DefectDojo aggregates security findings from all three repositories into a unified security dashboard:

```
📊 SECURITY FINDINGS AGGREGATION

🏗️ Infrastructure     📱 Application      🔄 GitOps
├─ Terraform scans   ├─ SAST (SonarQube) ├─ Policy violations
├─ AWS config        ├─ Secrets (Gitleaks)├─ Deployment risks  
└─ Network policies  ├─ Dependencies (Snyk)└─ Runtime issues
                     └─ Containers (Trivy)
                              │
                              ▼
                    🎯 DefectDojo Dashboard
                   ┌─────────────────────────┐
                   │ • Risk Prioritization   │
                   │ • Trend Analysis        │
                   │ • Compliance Reporting  │
                   │ • Remediation Tracking  │
                   └─────────────────────────┘
```

### **Security Metrics & Reporting**
- **📈 Vulnerability Trends**: Track security posture over time
- **🎯 Risk Prioritization**: CVSS scoring and business impact assessment  
- **📋 Compliance Reports**: Automated compliance framework mapping
- **🔄 Remediation Tracking**: Monitor fix progress across all repositories
- **⚡ Real-time Alerts**: Immediate notification of critical vulnerabilities

## 📊 Observability & Monitoring

### **Full-Stack Monitoring**

| Layer | Tool | Metrics Collected |
|-------|------|-------------------|
| **🏗️ Infrastructure** | Prometheus + Grafana | EKS cluster, nodes, pods, AWS resources |
| **📱 Applications** | ServiceMonitors | Microservice performance, health, SLIs |
| **🔄 GitOps** | ArgoCD Metrics | Deployment status, sync health, drift detection |
| **🛡️ Security** | DefectDojo + Istio | Vulnerability trends, policy violations, mTLS |
| **🌐 Network** | Istio + Jaeger | Service mesh traffic, distributed tracing |

### **Pre-configured Dashboards**
- **🎛️ Platform Overview**: Cross-repository health and status
- **🔒 Security Posture**: Vulnerability metrics and policy compliance
- **⚡ Performance**: Application SLIs, response times, error rates
- **🚀 Deployment**: GitOps sync status, rollout progress
- **🌐 Service Mesh**: Traffic flow, mTLS status, service dependencies

## 🔐 Security Architecture

### **Defense-in-Depth Strategy**

| Security Domain | Implementation | Cross-Repo Integration |
|-----------------|----------------|------------------------|
| **🌐 Edge Protection** | Route53 + cert-manager + Let's Encrypt | Automated SSL/TLS across all services |
| **🛡️ Network Security** | Istio service mesh + mTLS | Zero-trust communication |
| **⚖️ Policy Enforcement** | OPA Gatekeeper + constraints | Runtime validation of all deployments |
| **🔐 Secrets Management** | Vault + External Secrets + KMS | No hardcoded credentials anywhere |
| **👤 Identity & Access** | Pod Identity + RBAC + AWS IAM | Fine-grained permissions |
| **🔍 Code Security** | SAST + secrets detection + linting | Shift-left security practices |
| **📦 Container Security** | Image scanning + distroless builds | Secure container lifecycle |
| **📋 Audit & Compliance** | Git history + K8s logs + scan results | Complete audit trail |

### **Compliance Framework**

```
🔄 CONTINUOUS COMPLIANCE CYCLE

 Infrastructure Defines → GitOps Enforces → Applications Comply
        │                       │                    │
        ▼                       ▼                    ▼
   Policy Templates      Runtime Validation    Security Scans
   Security Baselines    Admission Control     Vulnerability Mgmt
   RBAC Definitions      Network Policies      Audit Logging
        │                       │                    │
        └───────────────────────┼────────────────────┘
                                │
                        📊 DefectDojo Reports
                       (Compliance Dashboard)
```

## 🔧 Platform Customization

### **Adding New Services**

#### **4-Step Integration Process**

```
1️⃣ APPLICATION REPO          2️⃣ GITOPS REPO
├─ Add service code          ├─ Create Kustomize manifests
├─ Create Dockerfile         ├─ Define networking rules
├─ Setup CI/CD workflow      ├─ Configure monitoring
└─ Enable security scans     └─ Set security policies
         │                            │
         ▼                            ▼
3️⃣ INFRASTRUCTURE REPO       4️⃣ INTEGRATION
├─ Update monitoring         ├─ Repository dispatch
├─ Add security policies     ├─ Automated deployments
└─ Extend observability      └─ End-to-end pipeline
```

### **Multi-Environment Strategy**

| Environment | Characteristics | Deployment Pattern |
|-------------|----------------|--------------------|
| **🧪 Development** | Single AZ, minimal resources | Direct GitOps sync |
| **🔬 Staging** | Production-like, full security | Manual promotion |
| **🚀 Production** | HA, auto-scaling, strict policies | Approval-based deployment |

### **Policy Management**

#### **Centralized Policy Framework**

```
🏗️ INFRASTRUCTURE → Defines base policies
           │
           ▼
🔄 GITOPS → Implements & enforces policies  
           │
           ▼
📱 APPLICATION → Complies with policies
           │
           ▼
🛡️ DEFECTDOJO → Monitors policy violations
```

| Policy Category | Scope | Enforcement Point |
|-----------------|-------|-------------------|
| **🔒 Security Constraints** | All deployments | OPA Gatekeeper |
| **🌐 Network Policies** | Service-to-service | Istio + NetworkPolicy |
| **👤 Access Control** | Cluster operations | EKS RBAC |
| **🔍 Scanning Requirements** | Build pipeline | CI/CD workflows |

## 📚 Repository Documentation

### **Detailed Guides**
- **🏗️ [Infrastructure Setup](./sec-eks-infra-automation/README.md)** - Complete EKS deployment guide
- **📱 [Application Development](./sec-online-boutique-appliation/README.md)** - Microservices and security scanning
- **🔄 [GitOps Configuration](./sec-gitops-online-boutique/README.md)** - Deployment and policy management

### **Best Practices & Standards**
- **[AWS EKS Best Practices](https://aws.github.io/aws-eks-best-practices/)** - Official AWS recommendations
- **[CNCF Security Whitepaper](https://github.com/cncf/sig-security/blob/master/security-whitepaper/CNCF_cloud-native-security-whitepaper-Nov2020.pdf)** - Cloud-native security
- **[GitOps Principles](https://opengitops.dev/)** - GitOps methodology
- **[DevSecOps Best Practices](https://www.devsecops.org/)** - Security integration patterns

## 🤝 Contributing

### **Repository-Specific Guidelines**
| Repository | Focus Area | Contribution Type |
|------------|------------|-------------------|
| **🏗️ Infrastructure** | Terraform modules, AWS resources | Infrastructure improvements |
| **📱 Application** | Microservices, security scanning | Feature development, security enhancements |
| **🔄 GitOps** | Kubernetes manifests, policies | Deployment configurations, policy updates |

### **Cross-Repository Changes**
For changes affecting multiple repositories:
1. Create issues in all affected repositories
2. Coordinate changes through pull requests
3. Test integration thoroughly
4. Update documentation across all repos

## 📄 License

This project is licensed under the **MIT License** - see individual repository LICENSE files for details.

---

## 🎯 Project Impact

**🌟 This platform demonstrates enterprise-grade DevSecOps practices with:**
- ✅ **Security-by-Design** - Multi-layer security embedded throughout
- ✅ **Full Automation** - End-to-end pipeline from code to production  
- ✅ **Zero-Trust Architecture** - No implicit trust, verify everything
- ✅ **Compliance-Ready** - Audit trails and policy enforcement
- ✅ **Production-Grade** - Scalable, monitored, and maintainable

**Built with ❤️ for DevSecOps education and enterprise adoption**