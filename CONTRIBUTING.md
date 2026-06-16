# Contributing to HR Analytics: Employee Attrition Prediction

Thank you for your interest in contributing! This document provides guidelines and instructions for contributing to this project.

## 📋 Table of Contents
- [Code of Conduct](#code-of-conduct)
- [How to Contribute](#how-to-contribute)
- [Development Setup](#development-setup)
- [Coding Standards](#coding-standards)
- [Commit Guidelines](#commit-guidelines)
- [Pull Request Process](#pull-request-process)

---

## 🤝 Code of Conduct

### Our Pledge
We are committed to providing a welcoming and inspiring community for all. Please be respectful and constructive in all interactions.

### Expected Behavior
- Use welcoming and inclusive language
- Be respectful of differing opinions and experiences
- Accept constructive criticism gracefully
- Focus on what is best for the community
- Show empathy towards other community members

### Unacceptable Behavior
- Harassment, discrimination, or intimidation
- Offensive comments or personal attacks
- Public or private harassment
- Publishing others' private information
- Any other conduct that violates professional standards

---

## 🎯 How to Contribute

### Types of Contributions

1. **Bug Reports:** Report issues and unexpected behaviors
2. **Feature Requests:** Suggest new features or improvements
3. **Code Improvements:** Optimize existing code
4. **Documentation:** Improve README, docstrings, comments
5. **Testing:** Add unit tests or improve test coverage
6. **Examples:** Create example notebooks or tutorials

### Reporting Bugs

**Before submitting a bug report:**
- Check if the issue already exists
- Collect relevant information (Python version, OS, error message)
- Test with the latest version

**Include in your bug report:**
```
**Description:** Clear description of the bug
**Environment:**
- Python version: [e.g., 3.8]
- OS: [e.g., Windows 10]
- Library versions: [pandas==1.5.3, scikit-learn==1.2.2]

**Steps to Reproduce:**
1. [First step]
2. [Second step]
3. [...]

**Expected Behavior:** [What should happen]
**Actual Behavior:** [What actually happens]
**Error Message:** [Full error traceback]

**Additional Context:** [Screenshots, code samples, etc.]
```

### Requesting Features

**Include in your feature request:**
```
**Description:** Clear description of the feature
**Use Case:** Why is this feature needed?
**Expected Behavior:** How should it work?
**Alternatives Considered:** [Any alternatives you've thought of]
**Additional Context:** [Mock-ups, examples, references]
```

---

## 🛠️ Development Setup

### 1. Fork the Repository
```bash
# Click "Fork" on GitHub
```

### 2. Clone Your Fork
```bash
git clone https://github.com/YOUR-USERNAME/HR-Analytics-Employee-Attrition-Prediction.git
cd HR-Analytics-Employee-Attrition-Prediction
```

### 3. Add Upstream Remote
```bash
git remote add upstream https://github.com/chavaganinagendrababu-ctrl/HR-Analytics-Employee-Attrition-Prediction.git
```

### 4. Create Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
```

### 5. Install Dependencies
```bash
pip install -r requirements.txt
pip install pytest pytest-cov black flake8  # Development tools
```

### 6. Create Feature Branch
```bash
git checkout -b feature/your-feature-name
```

---

## 📝 Coding Standards

### Python Style Guide
We follow **PEP 8** with the following guidelines:

```python
# ✅ Good
def calculate_attrition_probability(employee_data, model):
    """
    Calculate attrition probability for an employee.
    
    Parameters:
    -----------
    employee_data : dict
        Employee information
    model : sklearn model
        Trained prediction model
        
    Returns:
    --------
    float
        Probability of attrition (0-1)
    """
    features = preprocess_employee_data(employee_data)
    probability = model.predict_proba(features)[0][1]
    return probability


# ✅ Good - Clear naming and documentation
class AttritionPredictor:
    """Predict employee attrition using machine learning."""
    
    def __init__(self, model_path):
        self.model = self.load_model(model_path)
        self.scaler = StandardScaler()
```

### Code Quality Tools

**Format Code with Black:**
```bash
black .
```

**Check Style with Flake8:**
```bash
flake8 . --max-line-length=100
```

**Run Tests:**
```bash
pytest tests/ -v --cov=.
```

---

## 💬 Commit Guidelines

### Commit Message Format
```
<type>(<scope>): <subject>

<body>

<footer>
```

### Type
- `feat:` New feature
- `fix:` Bug fix
- `docs:` Documentation changes
- `style:` Code style (formatting, etc.)
- `refactor:` Code refactoring
- `perf:` Performance improvements
- `test:` Adding or updating tests
- `chore:` Maintenance tasks

### Examples

```bash
# Good commits
git commit -m "feat(model): implement XGBoost classifier"
git commit -m "fix(preprocessing): handle missing values in categorical features"
git commit -m "docs(readme): add installation instructions"
git commit -m "refactor(utils): simplify data loading function"
git commit -m "test(model): add unit tests for prediction accuracy"
```

### Commit Best Practices
- Write clear, descriptive messages
- Use imperative mood ("add" not "added")
- Limit subject line to 50 characters
- Explain what and why, not how
- Reference related issues: "Fixes #123"

---

## 🔄 Pull Request Process

### Before Submitting

1. **Update your branch:**
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

2. **Run tests:**
   ```bash
   pytest tests/ -v
   ```

3. **Check code quality:**
   ```bash
   black .
   flake8 .
   ```

4. **Create a clear commit:**
   ```bash
   git add .
   git commit -m "feat(model): add model improvement"
   ```

### Submit Pull Request

1. **Push to your fork:**
   ```bash
   git push origin feature/your-feature-name
   ```

2. **Create PR on GitHub** with the following template:

```markdown
## Description
Clear description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Code improvement

## Related Issues
Fixes #123

## Testing
- [ ] Unit tests added/updated
- [ ] Manual testing completed
- [ ] Code quality checks passed

## Checklist
- [ ] My code follows the style guidelines
- [ ] I have updated documentation
- [ ] I have added/updated tests
- [ ] All tests pass locally
- [ ] No new warnings generated
```

### PR Review Process

**What to expect:**
- Code review by maintainers
- Feedback and suggestions
- Requests for improvements
- Approval and merge

**Address feedback:**
- Respond to all comments
- Make requested changes
- Re-push updates
- Avoid force pushes after review

---

## 📚 Documentation Standards

### Docstring Format (Google Style)

```python
def predict_attrition(model, features):
    """
    Predict employee attrition based on input features.
    
    Args:
        model: Trained machine learning model
        features (pd.DataFrame): Employee feature matrix
        
    Returns:
        np.ndarray: Predicted attrition probabilities (0-1)
        
    Raises:
        ValueError: If features have incorrect shape
        
    Example:
        >>> model = load_model('attrition_model.pkl')
        >>> features = prepare_features(data)
        >>> predictions = predict_attrition(model, features)
    """
    if features.shape[1] != model.n_features_in_:
        raise ValueError("Feature count mismatch")
    
    return model.predict_proba(features)[:, 1]
```

---

## 🧪 Testing Guidelines

### Writing Tests

```python
# tests/test_model.py
import pytest
from sklearn.datasets import make_classification
from models import AttritionPredictor

class TestAttritionPredictor:
    """Test suite for AttritionPredictor."""
    
    @pytest.fixture
    def sample_data(self):
        """Fixture providing sample test data."""
        X, y = make_classification(n_samples=100, n_features=20)
        return X, y
    
    def test_model_initialization(self):
        """Test model initialization."""
        model = AttritionPredictor()
        assert model is not None
    
    def test_prediction_shape(self, sample_data):
        """Test prediction output shape."""
        X, y = sample_data
        model = AttritionPredictor()
        model.train(X, y)
        predictions = model.predict(X[:10])
        assert predictions.shape == (10,)
    
    @pytest.mark.parametrize("n_samples", [10, 50, 100])
    def test_predictions_bounds(self, n_samples):
        """Test predictions are in valid probability range."""
        X = create_dummy_data(n_samples)
        model = AttritionPredictor()
        predictions = model.predict_proba(X)
        assert all(0 <= p <= 1 for p in predictions)
```

**Run tests:**
```bash
# Run all tests
pytest

# Run specific test file
pytest tests/test_model.py

# Run with coverage
pytest --cov=. --cov-report=html
```

---

## 🎓 Resources

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Flow Guide](https://guides.github.com/introduction/flow/)
- [PEP 8 Style Guide](https://www.python.org/dev/peps/pep-0008/)
- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html)
- [Semantic Versioning](https://semver.org/)

---

## ❓ Questions?

- Check existing issues and discussions
- Open a new discussion
- Contact project maintainers

---

## 🙏 Thank You!

Your contributions are valuable and appreciated. Together, we're building better tools for HR analytics!

---

**Last Updated:** June 2026
**Maintained By:** Chavagani Nagendra Babu
