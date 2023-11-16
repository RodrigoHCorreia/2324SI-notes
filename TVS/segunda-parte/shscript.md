# ShellScript language details

definir variáveis com valores por omissão

```bash
var=${var:-default}
```

para fazer um id é com parêntesis retos [ ] e segue a seguinte sintaxe:

```bash
if [ -f ./aux-log-message.sh ]; then
    . ./aux-log-message.sh
else
    echo "aux-log-message.sh not found"
    exit 1
fi
```

um for é :

```bash
for PORT in $PORTS; do
    echo "Port $PORT is open"
done
```

para instânciar um link simbólico é (não somente para shell script mas para linux em geral):

```bash
ln -s ORIGINAL_FILE LINK_NAME
```
