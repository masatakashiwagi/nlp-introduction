# Chapter5-2
## 特徴エンジニアリング
- 自然言語処理の分野では、特徴のことを素性と呼んだりする
- 特徴
	- 質的変数
		- 名義尺度
			- 順番に意味が無い
			- カテゴリー
		- 順序尺度
			- 順番に意味がある
			- 間隔には意味が無い
	- 量的変数
		- 間隔尺度
			- 順番に意味がある
			- 間隔は等間隔で意味がある
			- ゼロに相対的な意味がある
		- 比例尺度
			- 順番に意味がある
			- 間隔は等間隔で意味がある
			- ゼロに絶対的な意味がある

# Chapter5-3
## テキストのベクトル表現
- 機械学習モデルにデータを与えるためには、テキストをベクトルに変換する必要がある
- テキストをベクトル化する方法
	1. 単語の分割
	2. ベクトル化
		- N-gramベクトル
			- 連続するn個のトークン（単語や文字など）のこと
				- n=1の時、ユニグラム（uni-gram）
				- n=2の時、バイグラム（bi-gram）
			- サンプル: the cat is out of the bagの場合
				- n=1: 'the', 'cat', 'is', 'out', 'of', 'the', 'bag'
				- n=2: 'the cat', 'cat is', 'is out', 'out of', 'of the', 'the bag'
			- n-gramに対して、重複の無いように数値を割り当てる -> vocabularyという
				- 語彙を作成したら、Bag-of-Ngrams（BoW）と呼ばれる形式でベクトル表現にする
					- テキストにn-gramが含まれているか否かだけを考えるモデル
						- n=1の場合のBoWを対象に、以下を考える
							- One-hotエンコーディング
							- Countエンコーディング
								- ある単語がテキストに存在するか否かだけでなく、その頻度を考慮してベクトルを作成する
									- 頻度が高い単語を重要視するようなベクトルができる
							- th-idf
								- 単語の出現頻度のみで重み付けすると、theのようなよく出るが、重要でない単語の重みが大きくなる
								- tf-idfでは、ある単語が出現する文書数の逆数idfを掛けて単語の重みを表現する
								- 頻繁に出現する単語を重要とみなしつつ、多くの文書に出現する単語は重要で無い
		- シーケンスベクトル