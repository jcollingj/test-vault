# React Performance Tips

## Common Performance Issues

### 1. Unnecessary Re-renders
**Problem**: Components re-render even when props haven't changed

**Solutions**:
- Use `React.memo()` for functional components
- Implement `useMemo()` for expensive calculations
- Use `useCallback()` for function props

```javascript
const MemoizedComponent = React.memo(({ data }) => {
  return <div>{data.title}</div>
})

const expensiveValue = useMemo(() => {
  return computeExpensiveValue(data)
}, [data])
```

### 2. Large Bundle Sizes
**Problem**: Slow initial load times

**Solutions**:
- Code splitting with `React.lazy()`
- Dynamic imports
- Tree shaking unused code
- Analyze bundle with webpack-bundle-analyzer

```javascript
const LazyComponent = React.lazy(() => import('./LazyComponent'))
```

### 3. Inefficient List Rendering
**Problem**: Rendering large lists is slow

**Solutions**:
- Use proper `key` props
- Implement virtualization (react-window, react-virtualized)
- Paginate or lazy load data

### 4. Heavy Computations in Render
**Problem**: Slow render cycles

**Solutions**:
- Move calculations outside render
- Use `useMemo()` for derived state
- Debounce expensive operations

## Profiling Tools

1. **React DevTools Profiler**
   - Visualize component render times
   - Identify unnecessary renders
   - Track component lifecycle

2. **Chrome DevTools**
   - Performance tab for detailed analysis
   - Memory profiler for leak detection
   - Network tab for bundle analysis

## Best Practices

1. ✅ Keep components small and focused
2. ✅ Avoid inline function definitions in JSX
3. ✅ Use production builds for performance testing
4. ✅ Implement proper error boundaries
5. ✅ Lazy load routes and heavy components
6. ❌ Don't optimize prematurely
7. ❌ Don't use memo everywhere (has cost too)

## When to Optimize

1. After profiling shows actual issues
2. User-reported performance problems
3. Slow interactions (> 100ms response)
4. Large data sets causing lag

Remember: "Premature optimization is the root of all evil"
