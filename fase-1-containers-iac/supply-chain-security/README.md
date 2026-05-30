# Supply Chain Security

**Objectivo:** Segurança na cadeia de fornecimento de software — scanning de vulnerabilidades e dependências  
**Custeamento:** Gratuito (ferramentas open source)

## Ferramentas abordadas
- Trivy — scanning de imagens e repositórios
- Snyk — análise de dependências (tier gratuito)
- Grype — scanner de vulnerabilidades
- OWASP Dependency-Track — gestão de SBOMs
- GitHub Dependabot — alertas automáticos

## Artefacto de portfólio
- Pipeline CI/CD com supply chain scanning (Trivy + Dependabot em GitHub Actions)

## Estrutura
- `notas/` — conceitos: SBOM, CVE, CVSS, supply chain attacks
- `labs/` — exercícios práticos com cada ferramenta
