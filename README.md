# Problem 3 - Email Alerts

---

# Email Alerts

**Email Alerts** is a Python package designed to send email notifications in development workflows. This tool can be used to send alerts during Continuous Integration/Continuous Deployment (CI/CD) processes or in any other scenario where notifications need to be sent via email. The package uses a local SMTP server for testing purposes and prints email messages to the console without actually sending them to the recipient.

## Features

- Send email alerts from one user to another using a local SMTP server.
- Customize the sender, recipient, subject, and body of the email.
- Useful for debugging and testing email notifications in development environments.

---

## Installation

### Prerequisites

- Python 3.11 or later
- [Poetry](https://python-poetry.org/docs/#installation) installed for dependency management

### Setup Instructions

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd Problem3
   ```

2. **Install dependencies using Poetry**:
   Make sure you are in the `Problem3` directory and run:
   ```bash
   poetry install
   ```

3. **Activate the virtual environment**:
   ```bash
   .\.venv\Scripts\activate  # On Windows
   source .venv/bin/activate  # On macOS/Linux
   ```

---

## Usage

To test the email alert system, you first need to run a local SMTP debugging server, and then you can run the `alert.py` script to send an email.

### 1. Start the SMTP Debugging Server:

In a separate terminal window, run:
```bash
python -m smtpd -n -c DebuggingServer localhost:1025
```
Keep this terminal open, as this will capture the email messages for debugging.

### 2. Send an Email:

Now, in another terminal (while keeping the SMTP server running), use the following command to send a test email:

```bash
python src/email_alerts/alert.py -s "sender@example.com" -r "recipient@example.com" -j "Test Subject" -b "This is a test email body"
```

You should see the email contents printed in the terminal where the SMTP server is running.

### Command Line Options:

- `-s` or `--sender`: The email address of the sender (required).
- `-r` or `--recipient`: The email address of the recipient (required).
- `-j` or `--subject`: The subject of the email (default: "Subject").
- `-b` or `--body`: The body of the email (default: "Body").

---

## Development

### Setting up Pre-commit Hooks

To ensure consistent code formatting, this project uses [Ruff](https://github.com/charliermarsh/ruff) as a formatter. Pre-commit hooks can be set up by running:

```bash
poetry run pre-commit install
```

To manually run the formatter on all files, use:
```bash
poetry run pre-commit run --all-files
```

---

## Continuous Integration

This project uses GitHub Actions for Continuous Integration (CI). The CI workflow performs the following steps:

1. Defines the operating system and Python version.
2. Installs Python and dependencies using Poetry.
3. Builds the documentation using Sphinx.
4. Installs and runs the pre-commit hooks.

The workflow is defined in the `.github/workflows/mailer-ci.yml` file.

---

## Documentation

Documentation for this project is built using [Sphinx](https://www.sphinx-doc.org/en/master/). To build the documentation:

1. Ensure Sphinx is installed:
   ```bash
   poetry add --dev sphinx
   ```

2. Build the documentation:
   ```bash
   poetry run sphinx-build -b html docs/ docs/_build/html
   ```

---

## License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for more details.

---

## Contributing

Feel free to submit issues or pull requests for any improvements or bug fixes. Contributions are welcome!

---

## Acknowledgements

This project is developed as part of the **DSAN_6700** course assignments at Georgetown University.

---


