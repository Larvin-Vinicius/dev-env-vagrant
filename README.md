Ambiente em maquina virtual com docker no debian 10

* Instale o vagrant
    * https://www.vagrantup.com/
* Instale o plugin para que possa vincular pastas locais na maquina virtual
    * `vagrant plugin install vagrant-vbguest` 

```bash
# Dentro da pasta inicie a maquina virtual e acesse a mesma via ssh 

vagrant up dev-env
vagrant ssh dev-env 
```
