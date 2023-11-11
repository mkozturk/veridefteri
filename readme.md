# Veri Defteri

## Kurulum
Site [Quarto](https://quarto.org/docs/get-started/) ile hazırlanmaktadır. Öncelikle bilgisayarınıza Quarto kurun ve çalıştırın.

VSCode kullanıyorsanız Quarto eklentisini kurmak kolaylık sağlar.

Bu repoyu bilgisayarınıza indirin

    $ gh repo clone mkozturk/veridefteri.com

Quarto, kod içeren belgeleri çalıştıracaktır. Bunun için bir hesaplama ortamı oluşturmak gerekiyor. Çalışma dizininde bir virtual environment yaratın ve aktifleştirin:

    $ cd veridefteri.com
    $ python -m venv .venv
    $ source .venv/bin/activate

Ardından `requirements.txt` kullanarak gerekli paketleri yeni sanal ortama kurun.

    $ pip install -r requirement.txt

Eğer yazınız için yeni bir kütüphane gerekiyorsa `requirements.txt` içine ekleyip işlemi tekrarlayın. Yeni halini github reposuna push etmeyi unutmayın.

## Yazının hazırlanması

Yazınızı önceden Markdown olarak hazırlayabilirsiniz. Quarto belgeleri [pandoc markdown](https://quarto.org/docs/authoring/markdown-basics.html) kullanır.

Jupyter notebook (`ipynb`) belgelerini de doğrudan alabilir. Web sitesini hazırlarken bunları HTML'ye dönüştürür.

### Dosya düzeni

Quarto, `posts/` dizini altındaki `.qmd` veya `.ipynb` belgelerini birer blog yazısına dönüştürür. Yeni bir yazı eklediğinizde, yazıyı ve ilgili belgelerini (resim, modül, data vs) bir altdizinle bunun altına koyun:

    posts/
        2022/
            blog_yazısı_1/
                blog_yazim.qmd
                fig1.png
                fig2.png
            blog_yazısı_2/
                ikinci_blog_yazim.qmd
        2023/
            hede_/
                hede_nedir.qmd
                img/
            hodo/
                neden_hodo.ipynb

Çok sık yazı yazmadığımız için yazıları yıllık bölümlere ayırmak yeterli. Ama hiç bölmemek bulmayı zorlaştırır. Bu dizin yapısının web sitesinin dizeniyle ilgisi olmayacak.

### Metaveriler
Her yazının en üstünde yazının başlığı, yazarı, tarihi ve kategorilerini belirten, üç çizgiyle başlayıp biten, YAML formatında metaveri bulunmalı. Örneğin

    ---
    title: Aşırı Öğrenme ve Eksik Öğrenme
    author: Birol Yüceoğlu
    date: '2017-11-07'
    categories:
        - yapay öğrenme
    ---

`posts/_metadata.yml` dosyasındaki metaveriler bütün yazılara uygulanır.

### Yazıyı görüntülemek

VSCode Quarto eklentisi kullanıyorsanız editör penceresinin sağ üstündeki "Preview" düğmesine tıklayın. Bu yazıyı (veya `index.qmd` içindeyseniz siteyi) tekrar render edip önizleme açacak.

Alternatif olarak, komut satırında

    $ quarto render

veya 

    $ quarto render yeni_yazim.qmd

komutlarını verebilirsiniz. Ardından 

    $ quarto preview

komutu, siteyi yerel olarak hazırlayıp bilgisayarınızda başlattığı bir sunucu ile bir ön izleme yapacak.

Alternatif olarak tarayıcınızda `_site/index.html` sayfasını açarak önizleme yapabilirsiniz.

## Yazıyı yayınlamak

Ayrıntıları site yayına hazır hale geldiği zaman belirleyeceğiz. Şimdilik düzenlenmiş yazıları repoya push edelim.