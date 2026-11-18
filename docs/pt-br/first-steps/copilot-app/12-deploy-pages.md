---
title: "Lição 12 - Implantar o site com o GitHub Pages"
description: "Use o aplicativo GitHub Copilot para configurar um fluxo de trabalho do Pages, revisar o pull request e verificar o Space Quiz publicado."
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

Publique o Space Quiz no GitHub Pages para que todos possam acessá-lo. O Copilot pode preparar o fluxo de trabalho e orientar a implantação, mas você continua responsável por revisar as alterações e confirmar que o site está disponível.

Nesta lição, você vai:

- pedir ao Copilot para configurar a implantação no GitHub Pages.
- revisar o fluxo de trabalho e o pull request antes de fazer o merge.
- acompanhar a implantação e verificar o site publicado.

## Cenário

O Space Quiz já está em um repositório do GitHub, mas ainda falta uma maneira simples de experimentá-lo. Publicar o site de arquivo único com o GitHub Pages o disponibiliza em uma URL pública sem adicionar um servidor ou dependência de runtime.

## Peça ao Copilot para preparar a implantação

> [!WARNING]
> Criar um pull request pode confirmar e enviar código. Revise as configurações de aprovação e o repositório de destino antes de enviar este prompt. Com **Approve all**, não espere outra solicitação de confirmação.

Na sessão do aplicativo Copilot para `space-quiz`, envie este prompt:

```plaintext
Prepare uma implantação no GitHub Pages para este repositório. Crie um fluxo de trabalho do GitHub Actions que faça o build do site, se necessário, e o implante no GitHub Pages depois que as alterações chegarem à branch padrão. Adicione um README que descreva o aplicativo e como executá-lo localmente, caso ainda não exista. Crie um pull request com essas alterações e informe o link e quaisquer configurações ou permissões necessárias do Pages. Não faça merge, não habilite o auto-merge, não altere as configurações do Pages nem implante o site. Pare e aguarde minha revisão.
```

## Revise o fluxo de trabalho e o pull request

1. Confirme se o README foi adicionado somente quando ainda não existia no repositório.
2. Revise as alterações do pull request, incluindo as etapas de build e implantação, os gatilhos e as permissões do fluxo de trabalho.
3. Confirme se o fluxo de trabalho implanta a partir da branch padrão, e não de um pull request que ainda não foi integrado.
4. Peça as correções necessárias e revise o diff atualizado. Aguarde a aprovação nas verificações obrigatórias do pull request antes de autorizar o merge.

## Autorize o merge e a implantação

> [!WARNING]
> O próximo prompt autoriza o agente a fazer merge do pull request revisado, alterar as configurações do Pages do repositório e publicar o site. Envie-o somente depois de concluir a revisão e confirmar o repositório e o pull request. Dependendo das configurações de aprovação, essas ações podem ocorrer sem outra solicitação de confirmação.

Substitua `<PR_NUMBER>` pelo número do pull request revisado e envie este prompt separadamente:

```plaintext
Revisei o pull request <PR_NUMBER> neste repositório e autorizo o merge e a implantação. Habilite o GitHub Pages usando o GitHub Actions, faça merge desse pull request somente depois que as verificações obrigatórias forem aprovadas e monitore a implantação até que ela seja concluída com sucesso. Informe a URL final do site publicado. Se você não tiver permissão para habilitar o Pages ou fazer merge, diga exatamente o que preciso aprovar ou fazer; não informe sucesso até que o site esteja no ar.
```

![Diagrama em três etapas: um pull request do space-quiz integrado; uma execução bem-sucedida de GitHub Actions Deploy website com as etapas Build website, Upload artifact e Deploy to Pages; e o Space Quiz publicado em yourname.github.io/space-quiz/.](../../../_images/first-steps-app-pages-deploy.svg)

## Verifique a implantação

1. Acompanhe a execução de implantação do GitHub Actions até a conclusão.
2. Abra a URL informada e confirme se o Space Quiz carrega.

Se o agente não puder habilitar o Pages ou fazer merge do pull request, siga as instruções específicas fornecidas. Não considere a tarefa concluída até a implantação ser concluída e o site publicado carregar.

## Resumo e próximas etapas

O Space Quiz está disponível como um site publicado, e você verificou a implantação em vez de confiar apenas no relato do agente. Continue para [Lição 13: Revisão e próximas etapas][next-lesson].

[next-lesson]: ../13-review/
