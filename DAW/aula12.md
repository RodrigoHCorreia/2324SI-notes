    # React

## Context

```tsx
<Component p="abc">
```

Componente recebe props, o mesmo tem estado interno e gera uma árvore de elementos.

Capacidade de mudar o caminho, sem produzir um recarregamento do documento.

https://example.com/users/123

Bookmark ou Deep-linking.

Ao fazer este pedido de get o resultado tem de ser um index.html

**history.pushState({}, "", "/users/123")**
**history.go(-1)** - Volta para a página anterior
**history.go(1)** - Avança para a página seguinte

React Router

```tsx
<Router>
    <Route path="/users/:id" component={UserDetails} />
</Router>
```

```tsx
function UserDetails() {
    const { id } = useParams();
    return <div>User {id}</div>
}
```

```tsx
function UserDetails() {
    const { id } = useParams();
    const history = useHistory();
    return (
        <div>
            User {id}
            <button onClick={() => history.go(-1)}>Back</button>
        </div>
    )
}
```

```tsx
function UserDetails() {
    const { id } = useParams();
    const history = useHistory();
    const [user, setUser] = useState(null);
    useEffect(
        () => {
            fetch(`https://example.com/users/${id}`)
                .then(response => response.json())
                .then(user => setUser(user))
        }, [id])
    return (
        <div>
            User {id}
            <button onClick={() => history.go(-1)}>Back</button>
            {user && <div>{user.name}</div>}
        </div>
    )
}
```

createBrowserRouter - um objeto que define as rotas. 

definimos um array de rota, e cada rota tem o path associado a essa rota e o elemento associado a essa rota.
no sitio onde metermos <Outlet \> vai ser renderizado os filhos que estão associados à rota.
de seguida tem childer, que são os filhos que estão associados a essa rota.