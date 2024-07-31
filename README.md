# [plopsec.com](https://plopsec.com)

**Because even DevSecOps deserve a break from the Command Line.**

Welcome to pl0pSec, a user-friendly, graphical interface designed to help you visualize your [Trivy](https://aquasecurity.github.io/trivy/) image scan reports effortlessly. This tool is crafted to offer DevSecOps professionals and enthusiasts a respite from the typical command-line operations without sacrificing the depth and reliability of security scanning.

## Features

**Web Interface**: Experience a clear and intuitive way to visualize your Trivy scan results via our web interface.
   - 🛡️ **Security Summary**: Get a quick overview of security findings including secrets and exploits counts.
     ![Security Summary Screenshot](docs/images/summary.png)
   
   - 🔑 **Secrets**: Discover a graphical representation of potential exposed secrets such as passwords, API keys, and tokens.
     ![Secrets Screenshot](docs/images/secrets.png)
   
   - 🎯 **Resources & Exploitability Metrics**: plopsec.com dynamically enhances Trivy findings with **daily updates** on exploitability metrics from EPSS, Exploit-DB, and Metasploit, keeping even static image scans relevant.
   
   - 🔍 **Filters**: Easily filter vulnerabilities by severity, fixability, and exploit availability, enhancing your security assessment.
     ![Resources Screenshot](docs/images/resources.png)
   
   - 🧱 **Layer Details**: Simplify troubleshooting by quickly identifying which layer and corresponding commands are introducing potential security weaknesses or secrets.
     ![Layer Details Screenshot](docs/images/layers.png)

🖱️ **Drag and Drop**: Effortlessly drag and drop your `.json` Trivy scan reports to view results.

⌨️ **CLI Integration**: Seamlessly send your Trivy scan reports from the command line to plopsec.com using our straightforward one-liner commands.

📅 **Flexible Report Management**: Tailor the expiry of scan reports and manage them easily through our web interface.

## Usage

### Option 1: Web Interface
Effortlessly drag and drop your `.json` Trivy scan reports on plopsec.com to view results immediately.

### Option 2: Command Line Options

Here are some ways you can use the command line to interact with plopsec.com:

1. **Basic Upload**
   ```bash
   trivy image --format json alpine:latest | gzip -c | curl -X POST -H "Content-Encoding: gzip" -H "Content-Type: application/json" --data-binary @- https://plopsec.com/api/v1/scan
   ```

2. **View Output and Upload**
   ```bash
   trivy image --format json alpine:latest | tee >(gzip -c | curl -X POST -H "Content-Encoding: gzip" -H "Content-Type: application/json" --data-binary @- https://plopsec.com/api/v1/scan)
   ```

3. **Proxy Support**
   ```bash
   trivy image --format json alpine:latest | gzip -c | curl -x http://username:password@yourproxy:port -X POST -H "Content-Type: application/json" --data-binary @- https://plopsec.com/api/v1/scan
   ```

## Contributing

pl0pSec is a personal project developed with enthusiasm and a community-first approach. Whether you're reporting bugs, suggesting enhancements, or proposing new features, your feedback is invaluable.

- [Report a bug](https://github.com/pl0psec/plopsec.com/discussions/new?category=bugs)
- [Enhance documentation](https://github.com/pl0psec/plopsec.com/discussions/new?category=documentation)
- [Request a feature enhancement](https://github.com/pl0psec/plopsec.com/discussions/new?category=ideas)

## Disclaimer

pl0pSec is maintained in my spare time, and while I strive to keep it up-to-date and feature-rich, I deeply value community input and collaboration. Let’s build a secure future together, enhancing pl0pSec one step at a time.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE) file for details.
