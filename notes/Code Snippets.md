# Code Snippets

## TypeScript Utilities

### Type-safe Event Emitter
```typescript
type EventMap = {
  userLogin: { userId: string; timestamp: number };
  dataUpdate: { id: string; data: Record<string, unknown> };
};

class TypedEmitter<T extends Record<string, unknown>> {
  private handlers: Map<keyof T, Set<(data: T[keyof T]) => void>> = new Map();

  on<K extends keyof T>(event: K, handler: (data: T[K]) => void) {
    if (!this.handlers.has(event)) {
      this.handlers.set(event, new Set());
    }
    this.handlers.get(event)?.add(handler as (data: T[keyof T]) => void);
  }

  emit<K extends keyof T>(event: K, data: T[K]) {
    this.handlers.get(event)?.forEach(handler => handler(data));
  }
}
```

### Debounce Hook
```typescript
function useDebounce<T>(value: T, delay: number): T {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const handler = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => clearTimeout(handler);
  }, [value, delay]);

  return debouncedValue;
}
```

## Bash Utilities

### Git Aliases
```bash
alias gst='git status'
alias gco='git checkout'
alias gcm='git commit -m'
alias gp='git push'
alias gl='git log --oneline --graph'
```
