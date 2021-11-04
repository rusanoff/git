# git

## Статьи

- [Пишем простейший GitHub Action на TypeScript / Хабр](https://habr.com/ru/post/561644/)
- [Вдарим по опенсорсу: как без страха прокачать свой аккаунт на Github](https://proglib.io/p/kak-vnesti-svoy-vklad-v-open-source-na-github-2020-02-02)



## Видео
- [Ускоряем разработку: GitHub Gist](https://www.youtube.com/watch?v=fUUXus8gGk0)



## Репозитории

- [Открытые API](https://github.com/public-apis/public-apis)
- [API браузеров 2020](https://github.com/luruke/browser-2020)


- [JS: Алгоритмы и структуры данных](https://github.com/trekhleb/javascript-algorithms)
- [JS: Список неплохих вопросов для собеседования](https://github.com/lydiahallie/javascript-questions/tree/master/ru-RU)
- [JS: Чистый код](https://github.com/ryanmcdermott/clean-code-javascript)


- [CSS: Советы](https://github.com/AllThingsSmitty/css-protips)


## Команды

### Элиасы для установки локального конфига

Создать функции в файле .zshrc

```bash
git_set_email() {
    git config --local user.email "$1";
}

git_set_name() {
    git config --local user.name "$1"
}

```

***

### Красивый список камитов

```bash
git log --graph --decorate --oneline
```

***

### Сделать squash commit

```bash
git reset --soft HEAD~N
```

N - количество комитов в ветке

После чего все изменения будут в local changes, их закомитить и сделать force push

***

### Переименовать ветку в origin

1. `git branch -m old_name new_name`

2. `git push origin :old_name new_name`

3. `git branch --set-upstream-to=origin/new_name new_name`

***

### Вывод ветки в командную строку на MacOS

Файл `.zshrc`:

```bash
parse_git_branch() {
    git branch 2> /dev/null | sed -n -e 's/^\* \(.*\)/[\1]/p'
}

setopt PROMPT_SUBST
export PROMPT='%F{grey}%n%f %F{cyan}%~%f %F{green}$(parse_git_branch)%f %F{normal}$%f '

```

***

### Вывод ветки в командную строку на Windows

Файл `.bashrc`:

```bash
function parse_git_branch {
  git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ \[\1\]/'
}

function prompt {
  local BLUE="\[\033[0;34m\]"
  local LIGHT_GREEN="\[\033[1;32m\]"
  local DEFAULT="\[\033[0m\]"
  export PS1="\h:\w \u$LIGHT_GREEN\$(parse_git_branch) $DEFAULT\$ "
}

prompt

```

Файл `.bash_profile`:

```bash
if [ -n "$BASH_VERSION" ]; then
    if [ -f "$HOME/.bashrc" ]; then
     . "$HOME/.bashrc"
    fi
fi

if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

umask 002

```

***

### Изменить удаленный адрес репозитория

```bash
git remote set-url origin LINK
```
