# Aula 13

**O systemd caracteriza as dependencias de duas formas:**

- Obrigatórias
- Opcionais

**Obrigatórias:**

- **Requires** - Se o serviço não estiver disponível, o serviço que o requer não será iniciado.
  
```bash
[Unit]
Description=My Service
Requires=unitfileThatMustBeRunning.service
```

**Opcionais:**

- **Wants** - Se o serviço não estiver disponível, o serviço que o quer não será iniciado, mas o serviço que o requer será iniciado.
  
```bash
[Unit]
Description=My Service
Wants=unitfileThatShouldBeRunning.service
```

É possível ainda ter dependências expressas de **forma inversa.**
Ou seja, se tiver um determinado x que depende de y, quem expressa a dependência pode ser o y e não o x.
Isto pode ser relevante por exemplo:
**Instalo um determinado software no sistema que tem um servico, e este serviço deve ser arrancado num determinado momento do meu sistema. há um dos targets (targets são os runlevels do systemd) que quando ativado, arranca o serviço.**

**RequiredBy**
**WantedBy**

Se o systemd precisa de algo vai ao /etc/systemd/system e procura, e se não houver vai procurar no /lib/systemd/system.

etc são defenidos posteriormente e lib são os que vêm diretamente com o sistema.

**Níveis de operacionalidade da máquina bottom-up:**

sysinit
basic
multi-user
graphical

```bash
[Unit]
Description=My Service

[Install]
WantedBy=multi-user.target
```
