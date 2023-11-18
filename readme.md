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

    (.venv)$ pip install -r requirement.txt

Eğer yazınız için yeni bir kütüphane gerekiyorsa `requirements.txt` içine ekleyip işlemi tekrarlayın. Yeni halini github reposuna push etmeyi unutmayın.

## Yazının hazırlanması

Yazınızı önceden Markdown olarak hazırlayabilirsiniz. Quarto belgeleri [pandoc markdown](https://quarto.org/docs/authoring/markdown-basics.html) kullanır.

Jupyter notebook (`ipynb`) belgelerini de doğrudan alabilir. Web sitesini hazırlarken bunları HTML'ye dönüştürür.

### Dosya düzeni

Quarto, `posts/` dizini altındaki `.qmd` veya `.ipynb` belgelerini birer blog yazısına dönüştürür. Yazılar
`posts/<yıl>/<ay>/<gün>/<yazı-basligi>/index.qmd` yapısıyla düzenlenmelidir. Örneğin

`posts/2017/10/30/jupyter-notebook-nedir/index.qmd`

Bu şekilde yazı, `veridefteri.com/posts/2017/10/30/jupyter-notebook-nedir/` URL'sinde yayınlanacak. Böylece orijinal Wordpress URL'lerimize yakın bir yapı olacak. (`posts/` parçası hariç)

Yazıyla ilgili dosyaları (resim, modül, data vs) yazıyla aynı dizine, veya bir altdizine koyabilirsiniz.

Jupyter belgesini `qmd`'ye çevirmek için:

`$ quarto convert my_notebook.ipynb --output index.qmd`

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

Siteyi Github Pages ile host edeceğiz. Yayınlama için ayrıntılı bilgi şurada:

https://quarto.org/docs/publishing/github-pages.html#publish-command
