package com.jd.answersearchtool.controller;

import com.jd.answersearchtool.model.Record;
import com.jd.answersearchtool.repository.RecordRepository;
import com.jd.answersearchtool.until.Upload;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;
import org.springframework.web.multipart.MultipartFile;

import java.io.File;
import java.io.IOException;
import java.util.List;

@CrossOrigin(origins = "*")
@RestController
public class RecordController {

    @Autowired
    private RecordRepository recordRepository;

    @RequestMapping(value = "/getRecords", method = RequestMethod.GET)
    public List<Record> getAll() {
        return recordRepository.findAll();
    }

    @RequestMapping(value = "/upload", method = RequestMethod.POST)
    public String Update(@RequestParam(name = "file") MultipartFile multipartFile) {
        System.out.println("数据开始更新");
        try {
            String path = new File("").getCanonicalPath() + "/upload";
            File file1 = new File(path);
            System.out.println(file1);
            if (!file1.exists()) {
                file1.mkdirs();
            }
            File file = new File(new File("").getCanonicalPath() + "/upload/" + multipartFile.getOriginalFilename());
            multipartFile.transferTo(file);
            List<Record> list = Upload.ReadXls(file);
            recordRepository.deleteAll();
            recordRepository.save(list);
            System.out.println("数据更新成功");
            return "{\"status\": \"success\"}";
        } catch (IOException e) {
            return "{\"status\": \"failed\"}";
        }
    }
}