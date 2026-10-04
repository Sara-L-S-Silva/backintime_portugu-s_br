<!--

SPDX-FileCopyrightText: © 2026 Back In Time Team

SPDX-License-Identifier: CC0-1.0

This file is released under Creative Commons Zero 1.0 (CC0-1.0) and part of

the program "Back In Time". The program as a whole is released under GNU

General Public License v2 or any later version (GPL-2.0-or-later).

See LICENSES directory or

go to <https://spdx.org/licenses/CC0-1.0.html>

and <https://spdx.org/licenses/GPL-2.0-or-later.html>.

-->

# Recomendações para testes manuais

Os testes automáticos não conseguem cobrir todos os cenários ou possíveis problemas. **Os testes manuais realizados por usuários reais garantem** que o *_Back In Time_* se comporte conforme o esperado. Eles fornecem ****insight, intuição e validação no mundo real****.

Pela experiência, os testes manuais do *_Back In Time_* são **extremamente valiosos, essenciais e absolutamente necessários**. Todo cenário do mundo real, caso extremo e interação sutil (especialmente nos diversos ambientes GNU/Linux) torna-se visível somente quando uma pessoa realmente executa a aplicação. Nenhum script automatizado, por mais completo que seja, consegue capturar totalmente essas nuances.

Os testes manuais são, portanto, ****insubstituíveis****: eles revelam bugs ocultos, peculiaridades da interface e problemas de fluxo de trabalho que só aparecem sob **condições autênticas de uso**. Cada feedback obtido em testes práticos melhora diretamente a confiabilidade, a usabilidade e a confiança dos usuários.

As recomendações a seguir ajudam a orientar os testes, mas usuários experientes podem naturalmente explorar fluxos de trabalho relevantes sem seguir instruções rígidas.

## Índice

<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

* [1. Configuração](#1-configuração)

* [2. Diretrizes gerais de teste](#2-diretrizes-gerais-de-teste)

* [3. Ações principais](#3-ações-principais)

* [4. Testes de agendamento](#4-testes-de-agendamento)

* [5. Testes da GUI](#5-testes-da-gui)

* [6. Observações](#6-observações)

<!-- TOC end -->

---

## 1. Configuração

* Instale o estado mais recente da branch `dev` do ****repositório git****. Se este teste for sobre um ****Release Candidate****, use o ****tarball do código-fonte**** disponível. Consulte as [instruções de instalação e dependências](CONTRIBUTING.md#build--install).

* Use uma ****máquina virtual nova ou um sistema limpo**** sem uma instalação anterior do *Back In Time*. Se você testar em sua máquina de produção, a recomendação mínima é usar a opção `--config=` para separar a configuração de teste da configuração habitual.

* Teste em diferentes distribuições GNU/Linux:

  * Principais linhas: Debian, Arch Linux (ou derivados)
  * Distribuição sem systemd: Devuan GNU/Linux

---

## 2. Diretrizes gerais de teste

* Sempre comece pelo ****terminal**** para detectar erros ou avisos silenciosos.

* Crie perfis de backup em todas as opções disponíveis:

  * ****Local****
  * ****SSH****

    * diferentes tipos de chaves ou simplesmente nenhuma chave de arquivo (configuração SSH do sistema)
    * chaves com e sem senha
    * senha armazenada em cache ou senha no keyring
    * Use um proxy SSH
  * Com e sem ****criptografia****

* Considere testar o *_Back In Time_* também em seu ****modo root****.

* Seria útil para a situação se você for um usuário regular do *_Back In Time_*.

---

## 3. Ações principais

* ****Criar um backup****

* ****Restaurar um backup****

* ****Excluir um backup****

* ****Excluir um perfil****

* ****Alterar o modo de um perfil existente****

---

## 4. Testes de agendamento

* ****Jobs do cron**** regulares (por exemplo, a cada 5 minutos)

* ****Agendamentos repetidos**** (execução semelhante ao anacron)

* ****Backups acionados por USB**** via udev (quando uma unidade é conectada)

---

## 5. Testes da GUI

* Abra todos os diálogos e interaja com eles; observe se ocorrem travamentos ou problemas de exibição.

* Experimente diferentes ambientes de desktop (por exemplo, MATE, Budgie).

* Experimente sistemas somente com Wayland.

* Verifique as traduções da GUI no(s) seu(s) idioma(s) nativo(s).

* Teste com substituições de tema do ****qt6ct****.

---

## 6. Observações

* Usuários experientes podem naturalmente explorar fluxos de trabalho adicionais além desta lista.

* Quaisquer ****bugs, travamentos ou comportamentos inesperados**** devem ser relatados nas [issues do projeto](https://github.com/bit-team/backintime/issues/new), incluindo logs, informações da versão ou informações de diagnóstico (use `--d iagnostics`) ou capturas de tela, se possível.
