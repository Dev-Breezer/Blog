# Java 集合案例之播放器管理



### 需求分析

> - **播放列表管理主要功能**
>   - 将歌曲添加到主播放列表
>   - 将歌曲添加到普通播放列表
>   - 通过歌曲id查询播放列表中的歌曲
>   - 通过歌曲名称查询播放列表中歌曲
>   - 修改播放列表中的歌曲
>   - 删除播放列表中的歌曲
>   - 显示播放列表中的所有功能



> - **播放器管理主要功能**
>   - 向播放器添加播放列表
>   - 从播放器删除播放列表
>   - 通过名字查询列表信息
>   - 显示所有播放列表的名称



### 详细设计

> 类:
>
> - 歌曲类( Song )
>
>   - 属性:歌曲id ( id )、歌曲名(name)、演唱者(singer)，均为字符串类型
>   - 方法︰
>     - 构造方法
>     - getter和setter方法
>     - hashCode() 、equals()方法和 toString()方法
>
> - 播放列表类(PlayList )
>
> - 属性∶
>
>   - 播放列表名称( playListName ) :字符串类型
>
>   - 播放列表中的歌曲集合( musicList ) : List类型
>   - 方法:-构造方法
>     - getter和setter方法
>   - 将歌曲添加到播放列表:
>     - public void addToPlayList(Song song);
>   - 显示播放列表中所有歌曲:
>     - public void displayAllSong();
>   - 通过id查询歌曲: 
>     - public Song searchSongByld(String id);
>   - -通过名称查询歌曲:
>     - public Song searchSongByName(String n);
>   - 修改歌曲: 
>     - public void updateSong(Stirng id,Song song);
>   - 从播放列表删除歌曲:
>     - public void deleteSong(String id);
>   - 按歌曲名进行排序: 
>     - public void sortBySongName();
>
> - 播放器类(PlayListCollection )
>
>   - 方法∶-构造方法
>     - getter和setter方法
>   - 添加播放列表:
>     - public void addPlayList(PlayList playList);
>   - 删除播放列名∶
>     - public PlayList searchPlayListByiae…
>   - 通过名字查询：
>     - public PlayList searchPlayListByName(String playListName);
>   - -显示所有播放列表名称: 
>     - public void displayPlayListName);
>
> - 测试类（TestDemo )



#### Song 类

```java
package com.demo.player;

import java.util.Objects;

/**
 * 歌曲类
 *
 * @author Breezer
 */

public class Song {
    private String id;  // 歌曲 id
    private String name; // 歌曲名
    private String singer; // 歌曲演唱者

    /**
     * 有参构造方法
     * @param id  存储歌曲 id
     * @param name 存储歌曲名
     * @param singer 存储演唱者
     */
    public Song(String id, String name, String singer){
        this.id = id;
        this.name = name;
        this.singer = singer;
    }

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getSinger() {
        return singer;
    }

    public void setSinger(String singer) {
        this.singer = singer;
    }

    /**
     * 重写 equals() 方法
     * @param o 比较对象
     * @return id,name,singer 相等则返回 boolean 值 true
     */
    @Override
    public boolean equals(Object o) {

        // 判断 Object 是否相等，相等则直接返回 true
        if (this == o) return true;
         if (!(o instanceof Song)) return false;
        Song song = (Song) o;
        return Objects.equals(id, song.id) && Objects.equals(name, song.name) && Objects.equals(singer, song.singer);
    }

    /**
     * 重写 hashCode() 方法
     * @return
     */
    @Override
    public int hashCode() {
        return Objects.hash(id, name, singer);
    }

    /**
     * 重写 toString() 方法
     * @return 返回字符串
     */
    @Override
    public String toString() {
        return "歌曲信息：id为：" + id  + ", 歌曲名称为：" + name + ", 演唱者为：" + singer ;
    }
}

```



#### PlayList 类

```java
package com.demo.player;

import java.util.ArrayList;
import java.util.List;

public class PlayList {
    private String playListName; // 播放列表名称
    private List<Song> musicList; // 播放列表中的歌曲集合

    /**
     * 构造方法
     * @param playListName 播放列表名称
     */
    public PlayList(String playListName){

        this.playListName = playListName;
        musicList = new ArrayList<>();
    }

    /**
     * 将歌曲添加到播放列表
     * @param song 要添加的歌曲
     */
    public void addToPlayList(Song song){
        // 要排除重复添加的情况
        boolean flag = false; // 判断播放列表中的歌曲是否存在
        for (Song song1:musicList){
            if(song1.equals(song)){
                flag=true;break;
            }
        }
        if (flag){
            System.out.println("该歌曲已经存在于播放列表中，添加失败");
        }else{
            musicList.add(song);
        }
    }

    /**
     * 通过歌曲 id 查询
     * @param id 歌曲id
     * @return 查询到的歌曲信息
     */
    public Song searchSongById(String id){
        Song song = null;
        // id 是唯一的
        for(Song s:musicList){
            if(s.getId().equals(id)){
                // 相等找到的结果
                song = s;break;
            }
        }
        return song;
    }

    /**
     * 根据歌曲名称查询
     * @param name 歌曲名称
     * @return 查询到的歌曲信息
     */
    public Song searchSongByName(String name){
        Song song = null;
        // id 是唯一的
        for(Song s:musicList){
            if(s.getName().equals(name)){
                // 相等找到的结果
                song = s;break;
            }
        }
        return song;
    }

    /**
     * 修改播放列表中的歌曲信息
     * @param id id 要修改的歌曲id
     * @param song 新的歌曲信息
     */
    public void updateSong(String id, Song song){
        // 根据 id 查询到相关的歌曲信息，然后再进行修改
        Song song1 = searchSongById(id);
        if(song1 == null){
            System.out.println("没有找到 id 为" + id + "对应的歌曲信息！");
        }else{
            // 先移除原来的歌曲信息，然后再重新添加
            musicList.remove(song1);
            musicList.add(song);
            System.out.println("修改成功！");
        }

    }

    /**
     * 删除播放列表中的指定的歌曲信息
     * @param id 歌曲 id
     */
    public void deleteSong(String id){
        Song song = searchSongById(id);
        if(song != null){
            musicList.remove(song);
        }else{
            System.out.println("没有找到 id 为" + id + "对应的歌曲信息！");
        }
    }

    /**
     * 显示播放列表中的所有歌曲
     */
    public void displayAllSong(){
        System.out.println("播放列表中的所有歌曲为：");
        for(Song song:musicList){
            System.out.println(song.toString()); // 此处写法与 System.out.println(song); 等效

        }
    }

}

```



#### Test 类

```java
package com.demo.player;

public class Test {
    // 对歌曲类 Song 进行测试
    public void testSong(){
        Song song1 = new Song("s001", "黑猫警长", "singer1");
        Song song2 = new Song("s002", "大角牛", "singer2");
        Song song3 = new Song("s003", "爱不会绝迹", "林俊杰");
        Song song4 = new Song("s003", "爱不会绝迹", "林俊杰");
        System.out.println(song1);

        // song1和song3是否相等
        System.out.println("song1==song3：" + (song1.equals(song3)));
        System.out.println("song3==song4：" + (song3.equals(song4)));
    }

    // 对播放列表类 PlayList 进行测试
    public void testPlayList(){

        // 定义Song类对象，添加到播放列表中
        Song song1 = new Song("s001", "黑猫警长", "singer1");
        Song song2 = new Song("s002", "大角牛", "singer2");
        Song song3 = new Song("s003", "爱不会绝迹", "林俊杰");
        Song song4 = new Song("s003", "爱不会绝迹", "林俊杰");

        // 创建 PlayList 对象
        PlayList mainPlayList = new PlayList("主播放列表");

        // 添加三首歌曲
        mainPlayList.addToPlayList(song1);
        mainPlayList.addToPlayList(song2);
        mainPlayList.addToPlayList(song3);
        mainPlayList.addToPlayList(song4); //添加重复的歌曲

        // 显示播放列表内容
        mainPlayList.displayAllSong();

        // 通过 id 查询查询歌曲信息
        Song song = mainPlayList.searchSongById("s002");
        if(song != null){
            System.out.println("根据id查询的歌曲信息为：");
            System.out.println(song);
        }else{
            System.out.println("该歌曲不存在！");
        }

        // 通过名称查询歌曲信息
        song = null;
        song = mainPlayList.searchSongByName("黑猫警长");
        if(song != null){
            System.out.println("根据name查询的歌曲信息为：");
            System.out.println(song);
        }else{
            System.out.println("该歌曲不存在！");
        }

        // 修改歌曲信息
        Song songUpdate = new Song("s005", "sold out", "singer5");
        mainPlayList.updateSong("s003",songUpdate);
        mainPlayList.displayAllSong();

        // 删除歌曲信息
        mainPlayList.deleteSong("s005");
        mainPlayList.displayAllSong();
    }

    public static void main(String[] args) {
        Test td = new Test();
        // td.testSong();
        td.testPlayList();
    }
}

```

