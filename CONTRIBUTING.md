# Contributing to Cut Video Editor

Thank you for your interest in contributing to Cut! 🎉

## Getting Started

1. **Fork the repository**
2. **Clone your fork**
   ```bash
   git clone https://github.com/YOUR_USERNAME/cut-video-editor.git
   cd cut-video-editor
   ```
3. **Install dependencies**
   ```bash
   pnpm install
   ```
4. **Start the dev server**
   ```bash
   pnpm dev
   ```

## Development Workflow

1. Create a feature branch from `main`
   ```bash
   git checkout -b feature/your-feature-name
   ```
2. Make your changes
3. Test thoroughly
4. Commit with clear, descriptive messages
5. Push to your fork
6. Open a Pull Request

## Code Style

- TypeScript for all new code
- Follow existing patterns in the codebase
- Use functional components with hooks
- Prefer descriptive variable names
- Add comments for complex logic

## Project Structure

```
src/app/
  ├── components/     # React components
  ├── hooks/          # Custom hooks
  ├── store/          # Zustand store
  └── App.tsx         # Main app component
```

## Key Technologies

- **React 18** - UI framework
- **TypeScript** - Type safety
- **Zustand** - State management
- **Immer** - Immutable state updates
- **Tailwind CSS** - Styling
- **Web APIs** - Canvas, Web Audio, IndexedDB

## Testing

Before submitting a PR:
- Test your changes in multiple browsers
- Ensure no console errors
- Verify the build works: `pnpm build`

## Areas for Contribution

### High Priority
- 🎥 **Video Export** - FFmpeg.wasm integration
- ✨ **Effects & Transitions** - Visual effects pipeline
- 🎵 **Audio Enhancements** - Volume controls, fades
- 🐛 **Bug Fixes** - Check open issues

### Medium Priority
- 📱 **Responsive Design** - Mobile/tablet support
- ♻️ **Performance** - Optimize rendering
- 🎨 **UI/UX** - Improve user experience
- 📚 **Documentation** - Code comments, guides

### Low Priority
- 🌍 **i18n** - Internationalization
- 🎭 **Themes** - Light mode, custom themes
- 🔌 **Plugins** - Plugin architecture

## Questions?

Feel free to open an issue for:
- Feature requests
- Bug reports
- Questions about the codebase
- Suggestions for improvements

Happy coding! 🚀