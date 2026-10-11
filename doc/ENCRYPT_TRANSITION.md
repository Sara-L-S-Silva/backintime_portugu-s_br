<!--
SPDX-FileCopyrightText: © 2024 Back In Time Team

SPDX-License-Identifier: GPL-2.0-or-later

This file is part of the program "Back In Time" which is released under GNU
General Public License v2 (GPLv2). See LICENSES directory or go to
<https://spdx.org/licenses/GPL-2.0-or-later.html>
-->

# Transição do recurso de encryption no _Back In Time_
<sub>Última atualização: junho de 2026</sub>

Este documento descreve o status do recurso de encryption. A partir da versão
[2.0.0] do _Back In Time_, o suporte a [EncFS] foi removido em favor do
[gocryptfs]. Consulte a
[meta issue #1734](https://github.com/bit-team/backintime/issues/1734) para
obter detalhes técnicos.

Talvez você esteja procurando a
[resposta sobre como acessar backups EncFS existentes sem usar o Back In Time](#como-acessar-backups-encfs-existentes-sem-usar-o-back-in-time).

 * [Justificativa](#justificativa)
 * [O processo de transição](#o-processo-de-transição)
 * [FAQ - Perguntas frequentes](#faq--perguntas-frequentes)
   * [Como migrar um EncFS backup profile para um gocryptfs backup profile?](#como-migrar-um-encfs-backup-profile-para-um-gocryptfs-backup-profile)
   * [Como acessar backups EncFS existentes sem usar o Back In Time](#como-acessar-backups-encfs-existentes-sem-usar-o-back-in-time)
 * [Sobre os problemas de segurança do EncFS](#sobre-os-problemas-de-segurança-do-encfs)
 * [Leituras e recursos adicionais](#leituras-e-recursos-adicionais)

## Justificativa
A remoção do [EncFS] foi necessária devido a [problemas de segurança conhecidos
desde 2014](#sobre-os-problemas-de-segurança-do-encfs). Além disso, o projeto
upstream não está mais ativo. Para manter o _Back In Time_ seguro e
manutenível, não havia alternativa à remoção.

## O processo de transição
A substituição do EncFS no _Back In Time_ foi [discutida pela
primeira vez](https://github.com/bit-team/backintime/issues/1248) em
2023. O plano foi elaborado para um período de transição mais longo, começando
em 2024 com avisos destacados para os usuários e terminando por volta de 2027
no upstream ou por volta de 2029, com o lançamento do Debian 14.

No entanto, o cronograma mudou e o lançamento upstream que introduziu essas
mudanças chegou antes do esperado, com a versão [2.0.0]. Essa versão também
provavelmente será incluída no [Debian GNU/Linux] 14 por volta de 2027.

O principal motivo é que integrar o gocryptfs como substituto do EncFS se
mostrou extremamente difícil devido à base de código do _Back In Time_, que
cresceu historicamente e é difícil de manter. Como resultado, foi necessário
antecipar a reestruturação e o refactoring já planejados para o mount
subsystem e os componentes relacionados. A remoção do suporte ao EncFS tornou-se
necessária como parte desse trabalho. A criação de novos EncFS profiles
[foi desabilitada](https://github.com/bit-team/backintime/issues/2315) na versão
[1.6.1], no início de 2026. É importante observar que, naquele momento, ainda
não havia suporte completo ao gocryptfs implementado.

## FAQ - Perguntas frequentes
### Como migrar um EncFS backup profile para um gocryptfs backup profile?

No próprio _Back In Time_, não é possível migrar um EncFS profile para um
gocryptfs profile. Também não é possível converter EncFS profiles existentes
em gocryptfs profiles.

É necessário criar um novo profile encrypted com gocryptfs. Consulte [esta
issue](https://github.com/bit-team/backintime/issues/2495) e [esta discussão
na mailing
list](https://mail.python.org/archives/list/bit-dev@python.org/message/ZYA6YRSCBIVLQTGR2VMNOQQIBA522AWI/)
para obter detalhes técnicos.

> [!NOTE]
> :wink: Se você conseguir fazer isso, seria muito útil contribuir com uma
> documentação semelhante a um tutorial para o projeto.


### Como acessar backups EncFS existentes sem usar o Back In Time

No momento, não há documentação oficial para acessar backups EncFS
existentes fora do _Back In Time_.

Sabe-se que o mecanismo subjacente funciona, mas ainda não foi documentado nem
verificado um procedimento claro, reproduzível e bem documentado.

O maintainer atual não tem recursos para trabalhar neste tópico e está
concentrando esforços em outras prioridades. No entanto, contribuições dos
usuários são bem-vindas: qualquer pessoa disposta a investigar o workflow,
documentar um processo confiável ou fornecer instruções passo a passo está
convidada a enviar uma proposta ou pull request.

Se a comunidade fornecer uma abordagem funcional e reproduzível, ela poderá
ser adicionada à documentação ou ao FAQ.

## Sobre os problemas de segurança do EncFS

- EncFS Security Audit
    - https://defuse.ca/audits/encfs.htm (como artigo atualizado no blog)
    - https://sourceforge.net/p/encfs/mailman/message/31849549/ (mensagem original na mailing list)
- [EncFS#314](https://github.com/vgough/encfs/issues/314) (uma meta issue **não corrigida** com uma lista de várias issues abertas relacionadas à Security Audit)
- [EncFS#659](https://github.com/vgough/encfs/issues/659)
- [EncFS#9](https://github.com/vgough/encfs/issues/9)
- [EncFS - Wiki de usuários do Ubuntu (alemão)](https://wiki.ubuntuusers.de/Archiv/EncFS)

## Leituras e recursos adicionais

- A meta issue [#1734](https://github.com/bit-team/backintime/issues/1734)
  sobre a transição, seu status atual e etapas e issues relacionadas.
- A primeira discussão concreta sobre a descontinuação do EncFS ocorreu em
  [#1549](https://github.com/bit-team/backintime/issues/1549). Mas o tópico
  começou bem antes
  (por exemplo, em [#1248](https://github.com/bit-team/backintime/issues/1248)).
- Nossa [mailing list](https://mail.python.org/mailman3/lists/bit-dev.python.org).
- Nossa [mailing list]
- [EncFS]
- [gocryptfs]

[EncFS]: https://github.com/vgough/encfs
[gocryptfs]: https://github.com/rfjakob/gocryptfs
[1.6.1]: https://github.com/bit-team/backintime/releases/tag/v1.6.1
[2.0.0]: https://github.com/bit-team/backintime/releases/tag/v2.0.0
[mailing list]: https://mail.python.org/mailman3/lists/bit-dev.python.org
[Debian GNU/Linux]: https://www.debian.org/