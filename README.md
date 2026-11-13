# MosaicEarth-Connector-DJITerra

DJI Terra Watch Folder daemon, GUI & CLI connector to auto-publish Orthomosaics, DSMs, 3D Tiles (terra_b3dm), LiDAR/dense point clouds, meshes & PDF reports to MosaicEarth.

## Releases & Ready-to-Install Downloads (`v0.4.0`)

- [`MosaicEarth-djiterra-0.4.0.zip`](https://github.com/nsicart/MosaicEarth-Connector-DJITerra/releases/download/v0.4.0/MosaicEarth-djiterra-0.4.0.zip)
- Also available directly from [MosaicEarth Desktop & Connectors (`app.mosaicearth.app/en/Desktop`)](https://app.mosaicearth.app/en/Desktop).

## Cloud & Local Workstation Endpoints

Every MosaicEarth connector speaks the open **MosaicEarth Synchronization Protocol v1** (chunked `4 MiB` resumable uploads + end-to-end `SHA-256` verification) and can connect to:

- **MosaicEarth Cloud** (default): `https://app.mosaicearth.app`
- **MosaicEarth Desktop (Local Workstation)**: `http://127.0.0.1:19771` (set `MOSAICEARTH_URL=http://127.0.0.1:19771` or select the endpoint in the connector UI).

## Usage & Setup

Download and extract `MosaicEarth-djiterra-0.4.0.zip` from [Desktop & Connectors](https://app.mosaicearth.app/en/Desktop).

- **Desktop GUI**: launch `djiterra_sync_mosaicearth.bat` (Windows) or `./djiterra_sync_mosaicearth.sh` (Linux), sign in, browse to your DJI Terra mission folder (or `PCGSPRO` workspace), and click **Synchronize Mission to MyEarth**.
- **Automatic Deliverable Classification**: discovers `map/result.tif` (`orthophoto`), `map/dsm.tif` (`elevation`), `models/pc/*/terra_b3dm/tileset.json` (bundled into `*_3dtiles.zip` with `metadata.xml`), `terra_las/*.las|*.laz` (`pointcloud`), `terra_obj/*.obj` (`.obj.zip` textured mesh), and `report/*.pdf` quality reports.
- **Watch Folder Daemon & CLI**:

```bash
python3 -m mosaicearth_djiterra.connector watch "D:/DJI_Terra/PCGSPRO" --project-id 42 --survey-name "Weekly Earthworks"
python3 -m mosaicearth_djiterra.connector push-folder "D:/DJI_Terra/PCGSPRO/Mission_20261112" --survey-date 2026-11-12
```

## License

Released under **GNU Affero General Public License v3.0 or later (`AGPL-3.0-or-later`)** — see [`LICENSE`](./LICENSE).
