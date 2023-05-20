FROM python:3.11.3-slim-bullseye
WORKDIR /build
ADD requirements.txt .
RUN <<EOF
	# install Git
	apt-get update
	apt-get install -y --no-install-recommends git

	# install python requirements
	python -m pip install --no-cache-dir --upgrade pip
	pip install --no-cache-dir -r requirements.txt

	# clean up
	apt-get autoremove -y # インストール後不要になった依存パッケージの削除
	apt-get clean # キャッシュされたデータの削除
	rm -rf /var/lib/apt/lists/* # apt-get updateで取得したパッケージのリストを削除
EOF