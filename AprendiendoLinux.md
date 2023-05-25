# AppImage



**Importancia: Mucha**

Forma que tienes para activar una aplicaciòn AppImage

```shell
chmod +x marktext-x86_64.AppImage

./marktext-x86_64.AppImage
```

Esto se elimina de la manera tradicional. Lo borras.

---

**Importancia:** *Poca*

Forma para crear acceso directo al escritorio. Requiere que hagas un código con los datos.

```shell
$ curl -L https://raw.githubusercontent.com/marktext/marktext/develop/resources/linux/marktext.desktop -o $HOME/.local/share/applications/marktext.desktop

# Update the Exec in desktop file to your real marktext command. Specify Path if necessary.
$ vim $HOME/.local/share/applications/marktext.desktop$ update-desktop-database $HOME/.local/share/applicati
```

---



# Flatpak

**Importancia: Mucha**

Forma que tienes para instalar desde Flatpak

```shell
flatpak install flathub com.github.marktext.marktext
```

Y si quieres actualizarlo debes usar

```shell
flatpak update
```
