# Publishing Checklist

## Pre-Publishing Steps

### 1. Update Project Details

- [x] Update author information in `pyproject.toml`
- [x] Update GitHub URLs in `pyproject.toml` with your actual repository
- [ ] Update version in `pyproject.toml` and `src/haystack/__init__.py`
- [ ] Update email in `pyproject.toml` with your contact email

### 2. Code Quality

- [x] Run `uv run black .` (formatting)
- [x] Run `uv run isort .` (import sorting)
- [x] Run `uv run mypy src/` (type checking)
- [x] Run `uv run pytest tests/ -v` (16 tests passing, including core logic)
- [x] Remove unused code and imports
- [x] Add proper docstrings

### 3. Documentation

- [x] Complete README.md with examples
- [x] Add CHANGELOG.md
- [x] Add LICENSE file
- [x] Update installation instructions

### 4. GitHub Repository Setup

- [ ] Create GitHub repository
- [ ] Push code to repository
- [ ] Set up branch protection for `main`
- [ ] Add repository description and topics

### 5. PyPI Setup

- [ ] Create PyPI account at https://pypi.org
- [ ] Generate API token in PyPI account settings
- [ ] Add `PYPI_API_TOKEN` secret to GitHub repository secrets

## Publishing Process

### Manual Publishing

```bash
# Build the package
uv build

# Upload to PyPI (requires twine)
pip install twine
twine upload dist/*
```

### Automated Publishing (Recommended)

1. Push a tag to trigger GitHub Actions:

```bash
git tag v0.1.0
git push origin v0.1.0
```

2. GitHub Actions will automatically:
   - Run tests
   - Build package
   - Publish to PyPI

## Post-Publishing

### 1. Verify Installation

```bash
pip install aws-haystack
haystack --help
```

### 2. Documentation

- [x] Update repository README with PyPI installation
- [x] Add badges to README (version, downloads, etc.)
- [ ] Consider adding documentation site

### 3. Community

- [ ] Add contributing guidelines
- [x] Set up issue templates
- [ ] Consider adding security policy

## Version Management

Update versions in these files when releasing:

- `pyproject.toml` - project version
- `src/haystack/__init__.py` - `__version__`
- `CHANGELOG.md` - new version entry
