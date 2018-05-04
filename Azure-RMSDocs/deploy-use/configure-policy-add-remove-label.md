---
title: Azure Information Protection ポリシーにラベルを追加または削除する
description: すべてのユーザー用のグローバル ポリシーまたはユーザーのサブセット用のスコープ ポリシーに Azure Information Protection ラベルを追加または削除します。
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/22/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0546cc11-67a5-4194-8c54-f3ac8ce9ebe1
ms.openlocfilehash: 73152d2202096775d315f874b30269c89213f8e1
ms.sourcegitcommit: 94d1c7c795e305444e9fde17ad73e46f242bcfa9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2018
---
# <a name="add-or-remove-a-label-to-or-from-an-azure-information-protection-policy"></a>Azure Information Protection ポリシーにラベルを追加または削除する

>*適用対象: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

>[!NOTE]
> この記事は、グローバル ポリシーまたはスコープ ポリシーからラベルを個別に作成できる、Azure Portal に対する最新の更新を反映しています。 また、ポリシーを公開するオプションは削除されます。 これらの変更に対してテナントがまだ更新されていない場合、たとえば Azure Information Protection に対して **[公開]** オプションがまだ表示され、**[分類]** メニュー オプションが表示されない場合は、数日待ってから以下の手順に戻ってください。  

Azure Information Protection ラベルを作成したら、ユーザーが使用できるようにラベルをポリシーに追加できます。 ラベルがすべてのユーザーに対するものである場合は、ラベルをグローバル ポリシーに追加します。 ラベルがユーザーのサブセットに対するものである場合は、ラベルをスコープ ポリシーに追加します。 現時点では、ラベルは 1 つのポリシーにのみ追加できます。 サブラベルを追加するには、親ラベルが同じポリシーまたはグローバル ポリシーにある必要があります。

既にポリシー内にあるラベルは、ポリシーから削除できます。 このアクションでは、ラベルは削除されません。 別のポリシーで利用可能なままになります。

ラベルをまだ作成していない場合は、「[Azure Information Protection の新しいラベルを作成する方法](configure-policy-new-label.md)」をご覧ください。

ラベルがユーザーのサブセットに適用されるようにスコープ ポリシーを作成する必要がある場合は、「[スコープ ポリシーを使用して特定のユーザーの Azure Information Protection ポリシーを構成する方法](configure-policy-scope.md)」をご覧ください。

## <a name="to-add-or-remove-a-label-to-or-from-a-policy"></a>ポリシーにラベルを追加または削除するには

1. まだサインインしていない場合は、新しいブラウザー ウィンドウを開き、[Azure Portal にサインイン](configure-policy.md#signing-in-to-the-azure-portal)します。 次に、**[Azure Information Protection]** ブレードに移動します。
    
    たとえば、ハブ メニューで **[すべてのサービス]** をクリックし、[フィルター] ボックスに「**Information**」と入力します。 "**Azure Information Protection**" を選択します。

2. **[分類]** > **[ポリシー]** メニュー オプションから: 追加または削除するラベルがすべてのユーザーに適用される場合は、**[Azure Information Protection]** - **[ポリシー]** ブレードで **[グローバル]** を選択します。

    追加または削除するラベルがユーザーのサブセットに適用される場合は、代わりにスコープ ポリシーを選択します。

3. **[ポリシー]** ブレードで、**[Add or remove labels]\(ラベルの追加または削除\)** を選択します。

4. **[Policy: Add or remove labels]\(ポリシー: ラベルの追加または削除\)** ブレードで、すべてのラベルが表示されて、ラベルがポリシーに既に存在する場合はチェック ボックスがオンになり、対応するポリシー名が **[ポリシー]** 列に表示されます。
     
    サブラベルはインデントされて表示されます。 スコープ ポリシーでは、グローバル ポリシーから継承されているラベルは利用不可として表示されます。
    
    次の 1 つ以上のアクションを実行し、**[OK]** をクリックします。
    
    - ラベルを追加するには、そのラベルを選択すると、オンになったチェックボックスが追加されます。
    
    - ラベルを削除するには、そのチェック ボックスをオフにします。
  
5. 変更を保存するには、**[保存]** をクリックします。
   
    変更内容はユーザーとサービスに対して自動的に利用可能になります。 独立した公開オプションはなくなりました。


## <a name="next-steps"></a>次の手順

Azure Information Protection ポリシーの構成の詳細については、「[組織のポリシーの構成](configure-policy.md#configuring-your-organizations-policy)」セクションのリンクを使用してください。  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]