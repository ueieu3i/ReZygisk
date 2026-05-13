# ReZygisk

[Español(Argentina)](/READMEs/README_es-AR.md)|[Bahasa Indonesia](/READMEs/README_id-ID.md)|[Português Brasileiro](/READMEs/README_pt-BR.md)|[Türkçe](/READMEs/README_tr-TR.md)|[Українська](/READMEs/README_uk-UA.md)|[Tiếng Việt](/READMEs/README_vi-VN.md)|

ReZygisk, KernelSU, APatch ve Magisk için Zygisk API desteği sağlayan bağımsız bir Zygisk uygulaması olan Zygisk Next'in bir çatalıdır (fork).

Kod tabanı tamamen C dilinde yeniden yazıldı; bu sadece takip etmesi daha kolay, çok daha temiz bir kod tabanı sağlamakla kalmıyor, aynı zamanda daha hızlı çalışan daha hafif derlenmiş dosyalar (binaries) sunuyor. ReZygisk'i gelecekteki tespitlere karşı korumak için özel bağlayıcılar (custom linkers) da tanıtıldı; normal şartlarda sistem bağlayıcısını hiç kullanmayarak bağlayıcı tabanlı tüm tespit yöntemlerini boşa çıkarır.

## Neden?

Zygisk Next'in en son sürümleri açık kaynak kodlu değildir ve kodlar tamamen geliştiricilerine aittir. Bu durum sadece projeye katkıda bulunma yeteneğimizi sınırlamakla kalmıyor, aynı zamanda Zygisk Next tüm sisteme erişimi olan ve süper kullanıcı (root) ayrıcalıklarıyla çalışan bir modül olduğu için, kodun denetlenmesini imkansız hale getirerek büyük bir güvenlik endişesi yaratıyor.

Zygisk Next geliştiricileri Android topluluğunda tanınmış ve güvenilirdir; ancak bu, kodun kötü amaçlı veya savunmasız olmadığı anlamına gelmez. Biz (PerformanC) kodu kapalı kaynak tutmak için kendi nedenleri olduğunu anlıyoruz, ancak bunun aksini savunuyoruz.

## Avantajlar

- FOSS (Sonsuza Dek Özgür ve Açık Kaynak)

## Bağımlılıklar

| Araç            | Açıklama                               |
|-----------------|----------------------------------------|
| `Android NDK`   | Android için Yerel Geliştirme Kiti     |

### C Bağımlılıkları

| Bağımlılık  | Açıklama                      |
|-------------|-------------------------------|
| `PLTI`      | Android için Basit PLT Hook'u |
| `CSOLoader` | SOTA Linux özel bağlayıcısı   |

## Kurulum

### 1. Doğru zip dosyasını seçin

ReZygisk'in ne kadar gizli ve stabil olacağını belirleyeceği için doğru sürümü/zip dosyasını seçmek önemlidir. Ancak bu zor bir işlem değildir:

- Çoğu durumda `release` sürümü seçilmelidir; uygulama düzeyindeki loglamayı (günlük kaydını) kaldırır ve daha optimize edilmiş derlenmiş dosyalar sunar.
- Bunun aksine `debug` sürümü ise ağır loglama içerir ve optimizasyon barındırmaz. Bu nedenle, **sadece hata ayıklama (debugging) amacıyla** ve **bir Sorun (Issue) açmak için log alırken** kullanmalısınız.

Dallara (branches) gelince, geliştiriciler tarafından aksi belirtilmedikçe veya gelecek özellikleri test etmek isteyip içerdiği risklerin farkında değilseniz, her zaman `main` (ana) dalı kullanmalısınız.

### 2. Zip'i flaşlayın

Doğru sürümü seçtikten sonra, Magisk veya KernelSU gibi mevcut root yöneticinizi kullanarak modülü flaşlamalısınız. Bunu, root yöneticinizin `Modüller` bölümüne giderek ve indirdiğiniz zip dosyasını seçerek yapabilirsiniz.

Flaşlama işleminden sonra, herhangi bir hata olmadığından emin olmak için kurulum günlüklerini kontrol edin ve her şey yolundaysa cihazınızı yeniden başlatabilirsiniz.

> [!WARNING]
> Magisk kullanıcıları yerleşik Zygisk'i devre dışı bırakmalıdır, aksi takdirde ReZygisk ile çakışacaktır. Bu işlem Magisk'in `Ayarlar` bölümüne gidip `Zygisk` seçeneği kapatılarak yapılabilir.

### 3. Kurulumu doğrulayın

Yeniden başlattıktan sonra, root yöneticinizin `Modüller` kısmındaki modül açıklamasına bakarak ReZygisk'in düzgün çalışıp çalışmadığını doğrulayabilirsiniz. Açıklama, gerekli arka plan programlarının (daemons) çalıştığını belirtmelidir. Örneğin, sisteminiz hem 64-bit hem de 32-bit destekliyorsa şuna benzer görünmelidir: `[Monitor: ✅, ReZygisk 64-bit: ✅, ReZygisk 32-bit: ✅] Standalone implementation of Zygisk.`

## Çeviri

ReZygisk için çevirilere katkıda bulunmanın şu anda iki farklı yolu vardır:

- README çevirileri için, `READMEs` klasörü içinde `<dil>` kısmının dil kodu olduğu `README_<dil>.md` adlandırma kuralını (örneğin Türkçe için `README_tr-TR.md`) izleyerek yeni bir dosya oluşturabilir ve değişikliklerinizle `main` dalına bir Pull Request (çekme isteği) açabilirsiniz.
- ReZygisk Web Arayüzü (WebUI) çevirileri için, öncelikle [Crowdin](https://crowdin.com/project/rezygisk) projemize katkıda bulunmalısınız. Onaylandıktan sonra oradan `.json` dosyasını alın ve değişikliklerinizle bir Pull Request açın -- `.json` dosyasını `webroot/lang` klasörüne, kendi isminizi de alfabetik sırayla `TRANSLATOR.md` dosyasına ekleyin.

## Destek

ReZygisk veya diğer PerformanC projeleriyle ilgili herhangi bir sorunuz için aşağıdaki kanallardan herhangi birine katılmaktan çekinmeyin:

- Discord Kanalı: [PerformanC](https://discord.gg/uPveNfTuCJ)
- ReZygisk Telegram Kanalı: [@rezygisk](https://t.me/rezygisk)
- PerformanC Telegram Kanalı: [@performancorg](https://t.me/performancorg)
- PerformanC Signal Grubu: [@performanc](https://signal.group/#CjQKID3SS8N5y4lXj3VjjGxVJnzNsTIuaYZjj3i8UhipAS0gEhAedxPjT5WjbOs6FUuXptcT)

## Katkı Sağlama

ReZygisk'e katkıda bulunmak için PerformanC'nin Güvenlik Politikası, Davranış Kuralları ve sözdizimi standartlarını içeren [Katkı Yönergelerini](https://github.com/PerformanC/contributing) izlemek zorunludur.

## Lisans

ReZygisk, [AGPL 3.0](./LICENSE) altında lisanslanmıştır. [Open Source Initiative](https://opensource.org/licenses/AGPL-3.0) üzerinden bu konuda daha fazla bilgi edinebilirsiniz.
