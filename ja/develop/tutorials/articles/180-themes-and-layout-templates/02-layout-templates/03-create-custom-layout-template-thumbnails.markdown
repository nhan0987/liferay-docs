---
header-id: creating-custom-layout-template-thumbnail-previews
---

# カスタムレイアウトテンプレートのサムネイルプレビューの作成

<p class="alert alert-info"><span class="wysiwyg-color-blue120">ご覧のページは、お客様の利便性のために一部機械翻訳されています。また、ドキュメントは頻繁に更新が加えられており、翻訳は未完成の部分が含まれることをご了承ください。最新情報は都度公開されておりますため、必ず英語版をご参照ください。翻訳に問題がある場合は、<a href="mailto:support-content-jp@liferay.com">こちら</a>までご連絡ください。</span></p>

[TOC levels=1-4]

あなたならば [ジェネレータテーマとレイアウトテンプレートを作成し](/docs/7-1/tutorials/-/knowledge_base/t/creating-layout-templates-with-the-themes-generator)、それはあなたのレイアウトテンプレートのプレビューサムネイルデフォルトを生成しました。 次の手順に従って、レイアウトテンプレートのカスタムプレビューサムネイルを作成します。

1.  コマンドラインを開き、レイアウトテンプレートの `docroot / layouttpl / custom` フォルダーに移動します。 Liferayテーマジェネレーターで作成されたテーマでレイアウトテンプレートを作成した場合、サムネイルはテーマの `src / layouttpl / custom` フォルダーにあります。

2.  サムネイルPNGファイルが存在する場合は、同じサイズ（120 x 120 px）のカスタムサムネイルPNGに置き換えるか、新しいPNGファイルを作成します。

3.  レイアウトテンプレートをテーマに含める場合、 `<thumbnail-path>` タグを使用して、テーマの `liferay-look-and-feel.xml`でサムネイルの場所を指定します。 以下は、Porygonテーマの構成例です。
   
        <layout-template id="porygon_50_50_width_limited" 
        name="Porygon 2 Columns (50/50) width limited">
            <template-path>
                /layoutttpl/custom/porygon_50_50_width_limited.ftl
            </template-path>
            <thumbnail-path>
                /layoutttpl/custom/porygon_50_50_width_limited.png
            </thumbnail-path>
        </layout-template>

レイアウトテンプレートをアプリサーバーに展開して使用します。 レイアウトテンプレートがテーマ</a>バンドルされている

場合、テーマがデプロイされるときにデプロイされます。 これで、@product@レイアウトテンプレートのカスタムサムネイルプレビューを作成する方法がわかりました！</p> 



## 関連トピック

[Liferayテーマジェネレーターを使用したレイアウトテンプレート](/docs/7-1/tutorials/-/knowledge_base/t/creating-layout-templates-with-the-themes-generator)

[レイアウトテンプレートを手動で作成する](/docs/7-1/tutorials/-/knowledge_base/t/creating-layout-templates-manually)

[テーマの作成](/docs/7-1/tutorials/-/knowledge_base/t/creating-themes)
