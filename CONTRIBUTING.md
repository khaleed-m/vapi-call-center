# Contributing to Vapi Call Center

Thank you for your interest in contributing to Vapi Call Center! This document provides guidelines and information for contributors.

## 🚀 Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/your-username/vapi-call-center.git
   cd vapi-call-center
   ```
3. **Install dependencies**:
   ```bash
   npm install
   ```
4. **Set up environment variables** (see README.md for details)
5. **Start the development server**:
   ```bash
   npm run dev
   ```

## 🔄 Development Workflow

### Branch Naming Convention
- `feature/description` - New features
- `fix/description` - Bug fixes
- `docs/description` - Documentation updates
- `refactor/description` - Code refactoring
- `test/description` - Adding or updating tests

### Commit Message Format
Follow the conventional commit format:
```
type(scope): description

[optional body]

[optional footer]
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples:**
```
feat(voice): add call recording functionality
fix(api): resolve phone number validation issue
docs(readme): update installation instructions
```

## 🧪 Testing

Before submitting a pull request:

1. **Test your changes** thoroughly
2. **Run the linter**:
   ```bash
   npm run lint
   ```
3. **Build the project**:
   ```bash
   npm run build
   npm run build:server
   ```

## 📝 Pull Request Process

1. **Create a feature branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes** and commit them with descriptive messages

3. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```

4. **Create a Pull Request** with:
   - Clear title and description
   - Reference any related issues
   - Screenshots/GIFs for UI changes
   - Test instructions

5. **Address review feedback** if requested

## 🎯 Areas for Contribution

We welcome contributions in these areas:

### 🚀 Features
- Enhanced voice interaction capabilities
- Additional call management features
- Integration with more webhook services
- Call analytics and reporting
- Multi-language support

### 🐛 Bug Fixes
- Voice connection issues
- UI/UX improvements
- Performance optimizations
- Cross-browser compatibility

### 📚 Documentation
- Code comments and documentation
- Tutorial content
- API documentation improvements
- Deployment guides

### 🧪 Testing
- Unit tests for components
- Integration tests for API endpoints
- End-to-end testing
- Performance testing

## 🎨 Code Style Guidelines

### TypeScript/JavaScript
- Use TypeScript for all new code
- Follow existing code formatting
- Use meaningful variable and function names
- Add JSDoc comments for complex functions
- Prefer functional components with hooks

### React Components
- Use functional components with hooks
- Implement proper error boundaries
- Follow the existing component structure
- Use proper TypeScript interfaces

### CSS/Styling
- Use Tailwind CSS classes
- Follow the existing design system
- Ensure responsive design
- Test across different screen sizes

## 🔒 Security Guidelines

- Never commit API keys or sensitive data
- Use environment variables for configuration
- Validate all user inputs
- Follow secure coding practices
- Report security issues privately

## 📞 Getting Help

If you need help or have questions:

1. **Check existing issues** on GitHub
2. **Create a new issue** with detailed information
3. **Join discussions** in existing issues
4. **Review the documentation** in README.md

## 🏆 Recognition

Contributors will be recognized in:
- GitHub contributors list
- Release notes for significant contributions
- Special mentions for outstanding contributions

## 📄 License

By contributing to Vapi Call Center, you agree that your contributions will be licensed under the MIT License.

---

Thank you for contributing to Vapi Call Center! 🎉