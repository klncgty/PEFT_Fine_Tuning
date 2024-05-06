Eğitilmiş büyük dil modellerinin tüm parametreleriyle Fine-tuning yapılması büyük maliyettir. 
PEFT ile modelin tüm parametreleri yerine yalnızca çok az sayıda model parametresine ince ayar yaparak olmasını istediğimiz davranış şeklini modele dikte edebiliriz.

Parameter efficient fine-tuning (PEFT), modellerin boyutunu küçültmeyi amaçlayan ve daha az güçlü GPU'larda hesaplamalar yapmayı mümkün kılan bir yöntemdir. 
LoRa, PEFT'de LLM'lerin boyutunu küçültmek için kullanılan bir yöntemdir.

PEFT, LoRA ve P-Tunign gibi adaptörlerle entegre edilmiştir. 
![Ekran görüntüsü 2024-05-06 075350](https://github.com/klncgty/PEFT_Fine_Tuning/assets/107580070/d31d3ae9-212b-4da0-9da1-350e4334c9cb)

Bu repoda çalışılan 2 adet PEFT metodu var. Birincisi reparameterization ( LoRA), ikincisi additive(p-tuning).

LoRA genelde eğitilebilir parametrelerin sayısını önemli ölçüde azalttığından tek bir GPU ile modeli fine tune etmek mümkün. 
![Ekran görüntüsü 2024-05-06 081439](https://github.com/klncgty/PEFT_Fine_Tuning/assets/107580070/203b4667-e0b4-4163-aba7-739269bbe406)

Bu kadar az parametre değişikliği ile büyük işlerin altından kalkması LoRA'yı çok cazip kılıyor. Bir de devasa GPU'lar gerekmiyor. İşte bu çok çok iyi.

Prompt tuning'e gelirsek, herhangi bir parametre değişikliği yapmadan modeli fine tune etmeye yarar. Peki nasıl oluyor ince ayar? Modele eklenen yeni katmanlar eğtiilmiş oluyor. Bu yüzden bu tekniğin adı
Additive. Yani prompt ile alakalı layerlar ekleyip bunları eğitiyoruz.
![maxresdefault](https://github.com/klncgty/PEFT_Fine_Tuning/assets/107580070/fe1470ba-7067-4a11-b6a4-8fff9b7fc7f4)

Gösterildiği gibi, prompt tuning, girdi promtına öğrenilebilir bir parametre ekleyerek, hedef görev için kaybı minimize etmek amacıyla optimize edilir. Bu, modelin belirli bir görev veya veri kümesine uyarlanmasına izin verir, ağırlıklarını güncellemek zorunda kalmaz. Prompt tuning, geleneksel fine-tuning'den daha maliyetsiz ve verimli olabilir, çünkü sadece promt parametresini güncellemek gerekir.

Referans ve ek döküman için 👇👇👇👇👇


```
@Misc{peft,
  title =        {PEFT: State-of-the-art Parameter-Efficient Fine-Tuning methods},
  author =       {Sourab Mangrulkar and Sylvain Gugger and Lysandre Debut and Younes Belkada and Sayak Paul and Benjamin Bossan},
  howpublished = {\url{https://github.com/huggingface/peft}},
  year =         {2022}
}
``` 

Nasıl çalıştığına dair detaylı açıklama ve araştırma-makaleler içeren link:
https://cameronrwolfe.substack.com/p/easily-train-a-specialized-llm-peft
