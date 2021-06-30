---
header-id: update-the-screenlet-class
---

# スクリーンレットクラスを更新する

<p class="alert alert-info"><span class="wysiwyg-color-blue120">ご覧のページは、お客様の利便性のために一部機械翻訳されています。また、ドキュメントは頻繁に更新が加えられており、翻訳は未完成の部分が含まれることをご了承ください。最新情報は都度公開されておりますため、必ず英語版をご参照ください。翻訳に問題がある場合は、<a href="mailto:support-content-jp@liferay.com">こちら</a>までご連絡ください。</span></p>

[TOC levels=1-4]

オフラインモードのScreenletクラスを更新するのは簡単です。 Screenletクラスの `onUserAction` メソッドで、Interactorの `start` メソッドの呼び出しを変更して、引数としてイベントのみを取るようにします。 ただし、これを行う前に、イベントインスタンスを作成し、そのキャッシュキーを設定する必要があります。 キャッシュキーは、ローカルキャッシュ内のエンティティを識別する値です。 これにより、後でサーバーと同期するためにキャッシュからエンティティを取得できます。

たとえば、ブックマークスクリーンレットの追加では、ブックマークのURLが適切なキャッシュキーになります。 オフラインモードをサポートするために、 `AddBookmarkScreenlet` の `onUserAction` メソッドは、ブックマークのデータを使用して新しい `BookmarkEvent` インスタンスを作成し、 `setCacheKey` メソッドを使用して、ブックマークのURLをイベントのキャッシュキーとして設定します。 Interactorのstartメソッドは、このイベントを引数として受け取ります。

    BookmarkEvent event = new BookmarkEvent(url, title, folderId);
    event.setCacheKey(url); 
    interactor.start(event);

オフラインモードを使用するためにキャッシュキーを設定する必要はありません。 代わりに、 `setCacheKey`を呼び出さずに、イベントを `start` メソッドに渡すことができます。 ただし、これは、キャッシュ内の最新のエンティティにのみアクセスできることを意味します。

それでおしまい\！ 書き込みスクリーンレットがオフラインモードをサポートするようになりました。 ただし、スクリーンレットを使用する際には、キャッシュをサーバーと同期することを念頭に置く必要があります。 次にこれについて学びます。

## 関連トピック

[イベントクラスを作成または更新する](/docs/7-1/tutorials/-/knowledge_base/t/create-or-update-the-event-class)

[リスナーを更新する](/docs/7-1/tutorials/-/knowledge_base/t/update-the-listener)

[インタラクタークラスを更新する](/docs/7-1/tutorials/-/knowledge_base/t/update-the-interactor-class)

[キャッシュをサーバーと同期する](/docs/7-1/tutorials/-/knowledge_base/t/sync-the-cache-with-the-server)
