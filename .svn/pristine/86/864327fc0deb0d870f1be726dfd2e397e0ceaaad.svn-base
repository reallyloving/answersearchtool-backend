package com.jd.answersearchtool.until;

import com.jd.answersearchtool.model.Record;
import org.apache.poi.ss.usermodel.Row;
import org.apache.poi.xssf.usermodel.XSSFSheet;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;

import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

/**
 * 操作Excel表格的功能类
 */
public class Upload {

    public static List<Record> ReadXls(File file) throws IOException {
        XSSFWorkbook wb = new XSSFWorkbook(new FileInputStream(file));
        List<Record> array = new ArrayList<>();
        XSSFSheet sheet = wb.getSheetAt(0);
        boolean body = false;
        int i = 1;
        for (Row row : sheet) {
            if (body) {
                Record record = new Record();
                record.setId(i);
                record.setFirstcategory(row.getCell(0).toString());
                record.setSecondcategory(row.getCell(1).toString());
                record.setThirdcategory(row.getCell(2).toString());
                record.setQuestion(row.getCell(3).toString());
                record.setType(row.getCell(4).toString());
                if (row.getCell(5) == null) {
                    record.setAnswer("");
                } else {
                    record.setAnswer(row.getCell(5).toString());
                }
                if (row.getCell(6) == null) {
                    record.setWebanswer("");
                } else {
                    record.setWebanswer(row.getCell(6).toString());
                }
                if (row.getCell(7) == null) {
                    record.setH5answer("");
                } else {
                    record.setH5answer(row.getCell(7).toString());
                }
                record.setFormtype("");
                array.add(record);
                i++;
            } else {
                body = true;
            }
        }
        return array;
    }
}
