# Taiso

## 📌 プロジェクト紹介

「taiso」は、一緒にサイクリングを楽しめるオフ会・コミュニティWebサービスです。

Github Repository [Link](https://github.com/SCIT46-1/taiso-web)

## 🛠 技術スタック

### Front-End  
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=white) ![TailwindCSS](https://img.shields.io/badge/TailwindCSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white) ![Zustand](https://img.shields.io/badge/Zustand-000000?style=for-the-badge&logo=zustand&logoColor=white) ![React Router](https://img.shields.io/badge/React--Router--DOM-CA4245?style=for-the-badge&logo=react-router&logoColor=white)

### Back-End  
![Java](https://img.shields.io/badge/Java%2017-007396?style=for-the-badge&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring%20Boot%203.x-6DB33F?style=for-the-badge&logo=springboot&logoColor=white) ![JPA](https://img.shields.io/badge/JPA%20/%20Hibernate-59666C?style=for-the-badge&logo=hibernate&logoColor=white)

### Database  
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)

### Version Control  
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)

### Tools  
![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white) ![Discord](https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white) ![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black) ![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)

## 👥 担当範囲

- **技術リード**

	- プロジェクト初期の技術スタック選定およびシステム設計

	- Git・GitHubを用いたバージョン管理戦略の策定

- **フロントエンド（担当割合：50%）**

	- **全体アーキテクチャおよびバックエンドとのインターフェース設計**

		- チーム開発に適したディレクトリ構成・設計方針の策定

	- **ページおよびコンポーネントのスタイリング**

		- Tailwind CSSとdaisy UIを活用した統一感のあるUI構築

		- グローバルモーダルの共通コンポーネント化と実装

	- **Zustandを用いたグローバル状態管理によるユーザー認証・認可ロジックとルート別アクセス制御の実装**

- **バックエンド（担当割合：30%）**

	- REST APIの設計・開発

	- Spring SecurityとJWTを活用したユーザー認証・認可機能の実装

## 🎯 主な機能

### 📍 ルート共有機能  
GPXファイルをアップロードし、地図上に表示・共有できます。人気のルートランキングも提供します。

### ⚡️ イベント（번개）開催・参加機能  
気軽にライドイベントを開催・募集し、「先着順」または「主催者承認制」で参加者を管理できます。  
タグ検索で好みに合ったイベントへの参加が可能です。

### 📊 Strava連携機能  
Strava APIを活用し、ユーザーの走行距離や平均速度などのライディングデータを表示できます。  
イベント参加時の走行記録も簡単に連動できます。

### 🏅 クラブ＆ブックマーク機能  
長期的なライディングクラブを運営でき、クラブメンバー限定イベントや専用掲示板での交流をサポートします。  
気になるルートやユーザーを非公開でブックマーク可能です。

## 🚀 開発のポイント & 工夫した点

### 外部地図API活用による経路画像最適化

GPXおよびTCXファイルから経路ポイントを抽出し、地図上に視覚化する機能を開発しました。

- 単一経路の詳細ページでは問題ありませんでしたが、複数の経路を一覧で表示するページでは数万個の座標データが必要となり、パフォーマンスの課題が発生しました。

- この問題を解決するため、バックエンドでGPXファイルアップロード時に自動的に経路の静的画像を生成してAWS S3に保存し、ユーザーへ提供する仕組みを構築しました。

- ユーザーは画像登録の手間が不要となり、GPXファイルの登録だけで簡単に経路情報を投稿可能になりました。

この実装により、バックエンドでの事前処理とフロントエンドでの迅速なデータ表示がサービスの性能とUX向上に効果的であることを学びました。

### Spring Security + JWT による認証・認可
大規模プロジェクトにおいて、Spring SecurityとJWTを使った認証・認可機能を担当しました。

JWTはHTTP Only属性付きのCookieでフロントエンドと安全に連携し、CORSやCSRFなどセキュリティ設定の強化も行いました。

フロントエンドではReact RouterにカスタムPrivateRouteを導入し、認証状態に応じたアクセス制御を実装しました。

Zustandを用いて認証情報をグローバルに管理し、ログイン状況に応じてUIを動的に変更し、ユーザー体験を改善しました。

また、LocalStorageを併用した認証情報の永続化やログアウト処理の実装により、UX向上にも努めました。

### チーム開発とリーダーシップ

6名規模のチームで設計〜開発〜運用まで全工程に関わりました。

- GitHub Flowに基づき、ブランチ戦略・PRレビュー・イシュー管理を実施

- 状態管理や共通コンポーネントの方針をリードし、設計段階での認識のずれを防ぐために積極的なコミュニケーションを心がけました

- Notion・Discordを活用し、開発後の振り返りやプロセス改善を行い、チーム文化の醸成にも貢献しました

## 📘 学んだこと

### 技術リーダーとしての技術選定と責任感
プロジェクト初期に技術リーダーとして技術スタックの選定やシステムアーキテクチャの設計を担当し、単なる技術選択にとどまらず、チーム全体の開発方針や協業体制を定義する責任の重さを実感しました。

フロントエンドとバックエンドの連携方法、状態管理の手法、認証・認可のフロー設計などにおいて、技術的な意思決定がプロジェクトの生産性や拡張性に大きな影響を与えることを深く理解しました。

この経験から、技術選定の際には短期的な利便性だけでなく、長期的な保守性やチームメンバーの理解度まで考慮する必要があると学びました。

### 中規模チームにおける GitHub ブランチ戦略の設計と運用

6人規模のチーム開発において、GitHub Flow をベースとしたブランチ戦略を設計・運用しました。

機能単位でブランチを切り、Pull Request を通じてコードレビューおよびマージを管理することで、コンフリクトの防止とコード品質の維持に貢献しました。

このような取り組みを通じて、リーダーシップだけでなく、健全なチーム文化の形成に必要な協業スキルの重要性を実感しました。

### ユーザー認証・認可を考慮した UX 設計

ユーザーのログイン状態や権限に応じた画面表示の切り替え、アクセス制御の UI 表現など、認証・認可を考慮した UX 設計を行いました。

具体的には、ルーティングレベルでのアクセス制御や、API トークンの有無による UI 状態の分岐などを設計し、セキュリティとユーザビリティのバランスを意識した実装を目指しました。

この経験を通じて、技術的な要件を満たしつつ、ユーザー視点での体験設計を行うことの難しさとやりがいを学びました。

## 📚 API Documentation

本プロジェクトでは以下の外部APIを活用しています：

### [Kakao地図 API](https://apis.map.kakao.com/)
- サイクリング経路のマップ表示や座標情報の取得に使用。
- 経路の可視化やイベントの位置情報表示に活用。

### [気象庁 API（KMA API Hub）](https://apihub.kma.go.kr/)
- サイクリング当日の天気情報を取得し、ユーザーに事前に表示。
- 天候によるイベント判断や安全性向上をサポート。

### [Strava API](https://developers.strava.com/)
- Stravaに記録されたアクティビティ情報を取得して登録
- ユーザーは手動で入力することなく、自分のデータを登録できます


## 📜 ライセンス

このプロジェクトは MITライセンス に基づいています。

## 🤝 感謝

ご協力いただいた全ての方々に心より感謝いたします。
