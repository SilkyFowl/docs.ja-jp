---
description: '詳細については、「タスク 2: ワークフローデザイナーをホストする」を参照してください。'
title: タスク 2:ワークフロー デザイナーのホスティング
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 5a00c9db831575dfe7f6f2b6e041f18877c60118
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755201"
---
# <a name="task-2-host-the-workflow-designer"></a>タスク 2:ワークフロー デザイナーのホスティング

このトピックでは、Windows Presentation Foundation (WPF) アプリケーションで Windows ワークフローデザイナーのインスタンスをホストする手順について説明します。

このプロシージャは、デザイナーを含む **Grid** コントロールを構成し、既定のアクティビティを含むのインスタンスをプログラムで作成し、デザイナーのメタデータを登録して、 <xref:System.Activities.Presentation.WorkflowDesigner> <xref:System.Activities.Statements.Sequence> すべての組み込みアクティビティのデザイナーサポートを提供し、WPF アプリケーションでワークフローデザイナーをホストします。

## <a name="to-host-the-workflow-designer"></a>ワークフロー デザイナーをホストするには

1. [「タスク 1: 新しい Windows Presentation Foundation アプリケーションを作成](task-1-create-a-new-wpf-app.md)する」で作成した HostingApplication プロジェクトを開きます。

2. ウィンドウのサイズを調整して、ワークフローデザイナーを簡単に使用できるようにします。 これを行うには、デザイナーで [ **mainwindow.xaml** ] を選択し、F4 キーを押して [ **プロパティ** ] ウィンドウを表示します。次に、[ **レイアウト** ] セクションで、[ **幅** ] を600に、[ **高さ** ] を350の値に設定します。

3. デザイナーで [**グリッド**] パネルを選択し ( **mainwindow.xaml** 内のボックスをクリック)、[**プロパティ**] ウィンドウの上部にある [**名前**] プロパティを "grid1" に設定して、グリッド名を設定します。

4. [ **プロパティ** ] ウィンドウで、プロパティの横にある省略記号 (**..**.) をクリックし `ColumnDefinitions` て、[ **コレクションエディター** ] ダイアログボックスを開きます。

5. [ **コレクションエディター** ] ダイアログボックスで、[ **追加** ] ボタンを3回クリックして、3つの列をレイアウトに挿入します。 最初の列には **ツールボックス** が含まれ、2番目の列はワークフローデザイナーをホストし、3番目の列はプロパティインスペクターに使用されます。

6. `Width`中央の列のプロパティを値 "4 *" に設定します。

7. **[OK]** をクリックして変更を保存します。 次の XAML が *mainwindow.xaml* ファイルに追加されます。

    ```xaml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. **ソリューションエクスプローラー** で、 *mainwindow.xaml* を右クリックし、[**コードの表示**] を選択します。 次の手順に従ってコードを修正します。

    1. 次の名前空間を追加します。

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. のインスタンスを保持するプライベートメンバーフィールドを宣言するには、 <xref:System.Activities.Presentation.WorkflowDesigner> クラスに次のコードを追加し `MainWindow` ます。

        ```csharp
        public partial class MainWindow : Window
        {
            private WorkflowDesigner wd;

            public MainWindow()
            {
                InitializeComponent();
            }
        }
        ```

    3. 次の `AddDesigner` メソッドを `MainWindow` クラスに追加します。 実装では、のインスタンスを作成し、 <xref:System.Activities.Presentation.WorkflowDesigner> アクティビティを追加して、 <xref:System.Activities.Statements.Sequence> grid1 **Grid** の中央の列に配置します。

        ```csharp
        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. デザイナーのメタデータを登録して、すべてのビルトイン アクティビティにデザイナー サポートを追加します。 これにより、ワークフローデザイナーの元のアクティビティにツールボックスからアクティビティをドロップでき <xref:System.Activities.Statements.Sequence> ます。 これを行うには、 `RegisterMetadata` メソッドをクラスに追加し `MainWindow` ます。

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        アクティビティデザイナーの登録の詳細については、「 [方法: カスタムアクティビティデザイナーを作成](how-to-create-a-custom-activity-designer.md)する」を参照してください。

    5. `MainWindow` クラス コンストラクターで、前に宣言したメソッドへの呼び出しを追加して、デザイナー サポートのメタデータを登録し、<xref:System.Activities.Presentation.WorkflowDesigner> を作成します。

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata.
            RegisterMetadata();

            // Add the WFF Designer.
            AddDesigner();
        }
        ```

        > [!NOTE]
        > `RegisterMetadata` メソッドは、<xref:System.Activities.Statements.Sequence> アクティビティを含むビルトイン アクティビティのデザイナーのメタデータを登録します。 `AddDesigner` メソッドは <xref:System.Activities.Statements.Sequence> アクティビティを使用するので、`RegisterMetadata` メソッドを先に呼び出す必要があります。

9. <kbd>F5</kbd>キーを押して、ソリューションをビルドして実行します。

10. 再ホストされたワークフローデザイナーに **ツールボックス** と **PropertyGrid** のサポートを追加する方法について [は、「タスク 3: ツールボックスと PropertyGrid のウィンドウを作成](task-3-create-the-toolbox-and-propertygrid-panes.md)する」を参照してください。

## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーのホスト変更](rehosting-the-workflow-designer.md)
- [タスク 1:新しい Windows Presentation Foundation アプリケーションの作成](task-1-create-a-new-wpf-app.md)
- [タスク 3:ツールボックス ペインと PropertyGrid ペインの作成](task-3-create-the-toolbox-and-propertygrid-panes.md)
