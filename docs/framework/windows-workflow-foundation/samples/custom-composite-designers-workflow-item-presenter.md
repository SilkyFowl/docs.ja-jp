---
description: 詳細については、「カスタム複合デザイナー-ワークフロー項目プレゼンター」を参照してください。
title: カスタム複合デザイナー - Workflow Item Presenter
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 20a3bddf7efd69b6138d6b8a5caae250aa377999
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787813"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>カスタム複合デザイナー - Workflow Item Presenter

<xref:System.Activities.Presentation.WorkflowItemPresenter>は、任意のアクティビティを配置できる "ドロップゾーン" の作成を可能にする WF デザイナープログラミングモデルのキーの種類です。 このサンプルでは、このような "ドロップゾーン" を格納するアクティビティデザイナーを構築する方法を示します。

このサンプルは次の方法を示します。

- <xref:System.Activities.Presentation.WorkflowItemPresenter> を使用したカスタム アクティビティ デザイナーの作成

- メタデータ ストアを使用したカスタム デザイナーの登録。

- 宣言および命令による再ホストされたツールボックスのプログラミング。

## <a name="sample-details"></a>サンプルの詳細

このサンプルのコードを次に示します。

- カスタム アクティビティ デザイナーは `SimpleNativeActivity` クラス用に作成されます。

- <xref:System.Activities.Presentation.WorkflowItemPresenter> を使用してカスタム アクティビティ デザイナーを作成します。

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
    <sap:ActivityDesigner.Resources>
        <DataTemplate x:Key="Collapsed">
            <StackPanel>
                <TextBlock>This is the collapsed view</TextBlock>
            </StackPanel>
        </DataTemplate>
        <DataTemplate x:Key="Expanded">
            <StackPanel>
                <TextBlock>Custom Text</TextBlock>
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                        HintText="Please drop an activity here" />
            </StackPanel>
        </DataTemplate>
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
            <Style.Triggers>
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>
    </sap:ActivityDesigner.Resources>
    <Grid>
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
    </Grid>
</sap:ActivityDesigner>
```

 `ModelItem.Body` にバインドする WPF のデータ バインディングの使用に注意してください。 `ModelItem` は、 <xref:System.Activities.Presentation.ActivityDesigner> デザイナーが使用されている基になるオブジェクト (この場合は **simplenativeactivity)**) を参照するのプロパティです。

## <a name="set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行する

1. Visual Studio でソリューションを開きます。

2. **F5** キーを押して、アプリケーションをコンパイルして実行します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`

## <a name="see-also"></a>関連項目

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [ワークフロー デザイナーを使用したアプリケーションの開発](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
