# pl0psec

**Because even DevSecOps deserve a break from the Command Line.**

## Project Description

Welcome to pl0pSec, a user-friendly, graphical interface designed to help you visualize your [Trivy](https://aquasecurity.github.io/trivy/) image scan reports effortlessly. This tool is crafted to offer DevSecOps professionals and enthusiasts a respite from the typical command-line operations without sacrificing the depth and reliability of security scanning.

## Features

- **Graphical Interface**: Visualize your Trivy scan results through a clear and intuitive web interface.
- **Drag and Drop**: Simply drag and drop your `.json` Trivy scan reports to view results.
- **CLI Integration**: Directly send your Trivy scan reports from the command line to pl0pSec with our easy-to-use one-liner commands.
- **Flexible Report Management**: Customize the expiry of scan reports and manage them conveniently through the web interface.

## Usage

### Web Interface

Navigate to the [pl0pSec website](https://plopsec.com) website and use the graphical interface to upload or view your Trivy scan reports.

### Command Line Options

Here are some ways you can use the command line to interact with pl0pSec:

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
   trivy image --format json alpine:latest | gzip -c | curl -x http://username:password@yourproxy:port -X POST -H "Content-Type: application/json" --data-binary @- https://plopsec.com/scan
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
